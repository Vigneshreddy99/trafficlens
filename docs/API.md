# TrafficLens API Documentation

## Overview

TrafficLens provides a Python API for integrating traffic analysis and behavioral insights into your applications.

## Table of Contents

- [Installation](#installation)
- [Quick Start](#quick-start)
- [Core Modules](#core-modules)
- [Traffic Classification](#traffic-classification)
- [Behavior Analysis](#behavior-analysis)
- [Feature Engineering](#feature-engineering)
- [Report Generation](#report-generation)
- [Examples](#examples)

---

## Installation

```bash
pip install -r requirements.txt
```

## Quick Start

```python
import pandas as pd
from traffic.classifier import TrafficClassifier
from behaviour.analysis import BehaviorAnalyzer
from pipeline.features import build_features

# Load your data
sessions = pd.read_csv('data/sessions.csv')
pageviews = pd.read_csv('data/pageviews.csv')

# Build features
features = build_features(sessions, pageviews)

# Classify visitors
classifier = TrafficClassifier()
classifications = classifier.classify(features)

# Analyze behavior
analyzer = BehaviorAnalyzer(sessions, pageviews)
insights = analyzer.analyze()

print(f"Detected {len(classifications)} visitors")
print(f"Found {len(insights['issues'])} behavioral issues")
```

---

## Core Modules

### 1. Traffic Classification (`traffic/`)

#### `TrafficClassifier`

Classifies visitors into Human, AI Agent, Bot, or Unknown.

```python
from traffic.classifier import TrafficClassifier

classifier = TrafficClassifier()
predictions = classifier.classify(features_df)
```

**Methods:**

##### `classify(features: pd.DataFrame) -> pd.DataFrame`

Classify visitors based on behavioral features.

**Parameters:**
- `features` (DataFrame): Feature matrix with columns:
  - `visitor_id`: Unique visitor identifier
  - `speed`: Pages per minute
  - `focus`: Page type concentration
  - `touch_rate`: Mobile touch interactions ratio
  - `returning`: Has visited before (bool)
  - `depth`: Pages per session
  - `duration`: Time on site (seconds)
  - `path_entropy`: Navigation randomness
  - `converted`: Completed purchase (bool)
  - `device_valid`: Device profile consistency (bool)

**Returns:**
- DataFrame with columns:
  - `visitor_id`: Visitor identifier
  - `predicted_type`: Human | AI_Agent | Bot | Unknown
  - `confidence`: 0.0 to 1.0
  - `reasoning`: Classification explanation

**Example:**

```python
features = pd.DataFrame({
    'visitor_id': ['V001', 'V002'],
    'speed': [2.5, 15.3],
    'focus': [0.6, 0.9],
    'touch_rate': [0.8, 0.0],
    'returning': [True, False],
    'depth': [8, 25],
    'duration': [180, 45],
    'path_entropy': [0.7, 0.2],
    'converted': [True, False],
    'device_valid': [True, False]
})

results = classifier.classify(features)
```

---

### 2. Behavior Analysis (`behaviour/`)

#### `BehaviorAnalyzer`

Analyzes user journeys and identifies behavioral issues.

```python
from behaviour.analysis import BehaviorAnalyzer

analyzer = BehaviorAnalyzer(sessions_df, pageviews_df)
results = analyzer.analyze()
```

**Methods:**

##### `analyze() -> dict`

Perform comprehensive behavioral analysis.

**Returns:**

Dictionary with keys:
- `journeys`: User journey graphs by visitor type
- `funnels`: Conversion funnel analysis
- `dead_ends`: Pages with high exit rates
- `loops`: Circular navigation patterns
- `rage_clicks`: User frustration indicators
- `hidden_pages`: Underutilized valuable pages
- `predictions`: Next-page predictions

**Example:**

```python
analyzer = BehaviorAnalyzer(sessions, pageviews)
insights = analyzer.analyze()

# Access specific analyses
dead_ends = insights['dead_ends']
print(f"Found {len(dead_ends)} dead-end pages")

for page in dead_ends:
    print(f"  {page['url']}: {page['exit_rate']:.1%} exit rate")
```

##### `get_journey_map(visitor_type: str) -> nx.DiGraph`

Get journey graph for specific visitor type.

**Parameters:**
- `visitor_type`: 'Human', 'AI_Agent', 'Bot', or 'Unknown'

**Returns:**
- NetworkX directed graph representing page transitions

**Example:**

```python
import matplotlib.pyplot as plt
import networkx as nx

human_journey = analyzer.get_journey_map('Human')
nx.draw(human_journey, with_labels=True)
plt.show()
```

---

### 3. Feature Engineering (`pipeline/`)

#### `build_features(sessions, pageviews) -> pd.DataFrame`

Build feature matrix from raw data.

**Parameters:**
- `sessions` (DataFrame): Session data with columns:
  - `visitor_id`
  - `session_id`
  - `start_time`
  - `end_time`
  - `device_type`
  - `source`
  
- `pageviews` (DataFrame): Pageview data with columns:
  - `visitor_id`
  - `session_id`
  - `page_url`
  - `timestamp`
  - `time_on_page`
  - `clicks`
  - `scrolls`
  - `touches` (mobile only)

**Returns:**
- DataFrame with engineered features

**Example:**

```python
from pipeline.features import build_features

features = build_features(sessions, pageviews)
print(features.columns.tolist())
```

#### Custom Feature Engineering

```python
from pipeline.features import FeatureBuilder

builder = FeatureBuilder(sessions, pageviews)

# Add custom features
builder.add_feature('avg_clicks_per_page', 
                   lambda df: df['total_clicks'] / df['total_pages'])

# Build
features = builder.build()
```

---

### 4. Anomaly Detection (`traffic/`)

#### `AnomalyDetector`

Detects traffic spikes and unusual patterns.

```python
from traffic.analysis import AnomalyDetector

detector = AnomalyDetector()
anomalies = detector.detect(sessions_df)
```

**Methods:**

##### `detect(sessions: pd.DataFrame) -> dict`

Detect anomalies in traffic patterns.

**Returns:**

Dictionary with keys:
- `spikes`: Traffic volume anomalies
- `source_issues`: Problematic traffic sources
- `scrapers`: Suspected scraping activity
- `fake_devices`: Spoofed device profiles

**Example:**

```python
detector = AnomalyDetector(threshold=3.0)  # 3 standard deviations
anomalies = detector.detect(sessions)

for spike in anomalies['spikes']:
    print(f"Spike detected at {spike['timestamp']}")
    print(f"  Volume: {spike['count']} visits ({spike['zscore']:.1f} σ)")
    print(f"  Source: {spike['source']}")
```

---

### 5. Report Generation (`agent/`)

#### `ReportGenerator`

Generate natural language insights from analysis results.

```python
from agent.report import ReportGenerator

generator = ReportGenerator()
report = generator.generate(traffic_results, behavior_results)
```

**Methods:**

##### `generate(traffic: dict, behavior: dict) -> str`

Generate markdown report with findings.

**Parameters:**
- `traffic`: Results from traffic analysis
- `behavior`: Results from behavior analysis

**Returns:**
- Markdown-formatted report string

**Example:**

```python
# Run analyses
traffic_results = classifier.classify(features)
behavior_results = analyzer.analyze()

# Generate report
generator = ReportGenerator()
report = generator.generate(
    traffic=traffic_results,
    behavior=behavior_results
)

# Save
with open('report/FINDINGS.md', 'w') as f:
    f.write(report)
```

##### `chat(query: str) -> str`

Interactive Q&A about findings.

**Parameters:**
- `query`: Natural language question

**Returns:**
- Answer based on analysis results

**Example:**

```python
generator = ReportGenerator()
generator.load_findings('report/FINDINGS.md')

answer = generator.chat("What is the main conversion issue?")
print(answer)
```

---

## Data Formats

### Sessions CSV

```csv
visitor_id,session_id,start_time,end_time,device_type,source,user_agent
V001,S001,2024-10-01 10:00:00,2024-10-01 10:15:30,desktop,google,Mozilla/5.0...
V002,S002,2024-10-01 10:01:15,2024-10-01 10:03:45,mobile,facebook,Mozilla/5.0...
```

### Pageviews CSV

```csv
visitor_id,session_id,page_url,timestamp,time_on_page,clicks,scrolls,touches
V001,S001,/home.html,2024-10-01 10:00:00,45.2,3,5,0
V001,S001,/products.html,2024-10-01 10:00:45,120.8,12,15,0
```

### Features CSV (Output)

```csv
visitor_id,speed,focus,touch_rate,returning,depth,duration,path_entropy,converted,device_valid
V001,2.5,0.6,0.0,true,8,930.5,0.72,true,true
V002,15.3,0.9,0.0,false,25,98.2,0.15,false,false
```

---

## Configuration

### `config.py`

```python
# Classification thresholds
HUMAN_SPEED_MAX = 5.0  # pages/minute
BOT_SPEED_MIN = 10.0

# Anomaly detection
SPIKE_THRESHOLD = 3.0  # standard deviations
MIN_SAMPLE_SIZE = 100

# Behavior analysis
DEAD_END_EXIT_RATE = 0.7  # 70%
RAGE_CLICK_THRESHOLD = 5  # clicks

# Report generation
CONFIDENCE_THRESHOLD = 0.8
MAX_FINDINGS = 20
```

---

## Error Handling

```python
from traffic.classifier import TrafficClassifier, ClassificationError

try:
    classifier = TrafficClassifier()
    results = classifier.classify(features)
except ClassificationError as e:
    print(f"Classification failed: {e}")
except ValueError as e:
    print(f"Invalid data format: {e}")
```

---

## Performance Tips

### 1. Batch Processing

```python
# Process in chunks for large datasets
chunk_size = 1000
results = []

for chunk in pd.read_csv('sessions.csv', chunksize=chunk_size):
    features = build_features(chunk, pageviews)
    predictions = classifier.classify(features)
    results.append(predictions)

final_results = pd.concat(results)
```

### 2. Caching

```python
from functools import lru_cache

@lru_cache(maxsize=128)
def cached_feature_build(sessions_hash, pageviews_hash):
    return build_features(sessions, pageviews)
```

### 3. Parallel Processing

```python
from multiprocessing import Pool

def process_visitor(visitor_data):
    features = build_features(*visitor_data)
    return classifier.classify(features)

with Pool(4) as pool:
    results = pool.map(process_visitor, visitor_chunks)
```

---

## Testing

```python
import pytest
from traffic.classifier import TrafficClassifier

def test_classification():
    classifier = TrafficClassifier()
    features = create_test_features()
    results = classifier.classify(features)
    
    assert 'predicted_type' in results.columns
    assert results['confidence'].between(0, 1).all()
    
def test_human_detection():
    features = create_human_features()
    results = classifier.classify(features)
    assert (results['predicted_type'] == 'Human').all()
```

---

## Advanced Examples

### Custom Classification Pipeline

```python
from traffic.classifier import BaseClassifier
from sklearn.ensemble import RandomForestClassifier

class CustomClassifier(BaseClassifier):
    def __init__(self):
        self.model = RandomForestClassifier(n_estimators=100)
        
    def fit(self, X, y):
        self.model.fit(X, y)
        
    def predict(self, X):
        predictions = self.model.predict(X)
        probabilities = self.model.predict_proba(X)
        return predictions, probabilities
```

### Real-time Classification

```python
import asyncio
from tracker.collector import EventCollector

async def realtime_classification():
    collector = EventCollector()
    
    async for event_batch in collector.stream():
        features = build_features_realtime(event_batch)
        classifications = classifier.classify(features)
        
        for visitor, type in classifications.iterrows():
            if type['predicted_type'] == 'Bot':
                await block_visitor(visitor['visitor_id'])
```

### Integration with Streamlit

```python
import streamlit as st
from traffic.classifier import TrafficClassifier

st.title("Real-time Traffic Classification")

uploaded_file = st.file_uploader("Upload sessions CSV")
if uploaded_file:
    sessions = pd.read_csv(uploaded_file)
    pageviews = pd.read_csv('pageviews.csv')
    
    if st.button("Analyze"):
        features = build_features(sessions, pageviews)
        results = TrafficClassifier().classify(features)
        
        st.dataframe(results)
        st.bar_chart(results['predicted_type'].value_counts())
```

---

## API Reference Summary

| Module | Class/Function | Purpose |
|--------|---------------|---------|
| `traffic.classifier` | `TrafficClassifier` | Visitor classification |
| `behaviour.analysis` | `BehaviorAnalyzer` | Journey analysis |
| `pipeline.features` | `build_features()` | Feature engineering |
| `traffic.analysis` | `AnomalyDetector` | Anomaly detection |
| `agent.report` | `ReportGenerator` | Report generation |
| `tracker.collector` | `EventCollector` | Data collection |

---

## Support

- **Documentation**: [GitHub Wiki](https://github.com/Vigneshreddy99/trafficlens/wiki)
- **Issues**: [GitHub Issues](https://github.com/Vigneshreddy99/trafficlens/issues)
- **Email**: 2320030126@klh.edu.in

---

**Last Updated**: October 29, 2024  
**Version**: 1.0.0
