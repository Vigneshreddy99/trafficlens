<div align="center">

# 🔍 TrafficLens
### AI-Powered Web Traffic & User Behavior Intelligence Platform

[![Live Demo](https://img.shields.io/badge/Demo-Live-success?style=for-the-badge)](https://trafficlens-cyrpftkfdrjyprq3wfehz4.streamlit.app/)
[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B?style=for-the-badge&logo=streamlit)](https://streamlit.io/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

**Advanced visitor classification, behavior analysis, and actionable insights for modern web applications**

[🚀 Live Demo](https://trafficlens-cyrpftkfdrjyprq3wfehz4.streamlit.app/) • [📖 Documentation](#documentation) • [🎯 Features](#key-features) • [⚡ Quick Start](#quick-start)

</div>

---

## 🎯 Problem Statement

Modern websites face critical challenges:
- **91.7% of web traffic** consists of bots and automated agents
- **$52 billion** in annual e-commerce losses due to bot fraud
- **Difficulty distinguishing** between legitimate AI assistants and malicious bots
- **Poor visibility** into why users abandon shopping carts (avg 69.8% abandonment rate)

## 💡 Our Solution

**TrafficLens** is an intelligent analytics platform that provides:

✅ **Automated Visitor Classification** - Distinguishes humans, AI agents, and bots with 92.7% accuracy  
✅ **Behavioral Fingerprinting** - 9-trait analysis for precise visitor profiling  
✅ **Real-time Anomaly Detection** - Identifies traffic spikes, scraping attempts, and fraud patterns  
✅ **Conversion Optimization** - Pinpoints friction points in user journeys  
✅ **AI-Generated Reports** - Natural language insights with evidence-backed recommendations  
✅ **Privacy-First Design** - No PII collection, GDPR compliant tracking

> **Note:** This project uses simulated data for demonstration and validation purposes, enabling honest accuracy scoring and reproducible results.

---

## 🌟 Key Features

<table>
<tr>
<td width="50%">

### 🤖 Traffic Classification
- **4-Category System**: Human, AI Agent, Bot, Unknown
- **Multi-layer Detection**: Behavior + Device + Pattern analysis
- **92.7% Accuracy** on known visitor types
- **Zero-day Detection**: Unknown bot flagging

</td>
<td width="50%">

### 📊 Behavior Analytics
- **Journey Mapping**: Visual user flow graphs
- **Conversion Funnel Analysis**
- **Rage Click Detection**
- **Dead-end Page Identification**

</td>
</tr>
<tr>
<td width="50%">

### 🔍 Anomaly Detection
- **Traffic Spike Alerts**
- **Source Quality Scoring**
- **Scraper Identification**
- **Fake Device Detection**

</td>
<td width="50%">

### 📈 Predictive Intelligence
- **Next-page Prediction**
- **Purchase Probability**
- **Traffic Forecasting**
- **Similarity Clustering**

</td>
</tr>
</table>

---

## ⚡ Quick Start

### Prerequisites
- Python 3.10 or higher
- pip package manager

### Installation

```bash
# Clone the repository
git clone https://github.com/Vigneshreddy99/trafficlens.git
cd trafficlens

# Install dependencies
pip install -r requirements.txt

# Run the complete analysis pipeline
python run_all.py

# Launch the dashboard
streamlit run streamlit_app.py
```

🌐 **Access the dashboard at:** `http://localhost:8501`

### Quick Demo (Pre-computed Results)

The repository includes pre-computed results. To view immediately:

```bash
streamlit run streamlit_app.py
```

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                          DATA COLLECTION                             │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐         │
│  │   Sessions   │───▶│  Pageviews   │───▶│  Event Data  │         │
│  └──────────────┘    └──────────────┘    └──────────────┘         │
└─────────────────────────────────────────────────────────────────────┘
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      FEATURE ENGINEERING                             │
│  • Behavioral Fingerprinting (9 traits)                             │
│  • Device & Network Patterns                                         │
│  • Temporal Analysis                                                 │
└─────────────────────────────────────────────────────────────────────┘
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      INTELLIGENCE MODULES                            │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐         │
│  │   Traffic    │    │   Behavior   │    │     Link     │         │
│  │  Classifier  │    │   Analyzer   │    │   Analyzer   │         │
│  └──────────────┘    └──────────────┘    └──────────────┘         │
└─────────────────────────────────────────────────────────────────────┘
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      AI REPORT GENERATION                            │
│  • Natural Language Insights                                         │
│  • Evidence-Backed Recommendations                                   │
│  • Interactive Q&A Chat                                              │
└─────────────────────────────────────────────────────────────────────┘
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                     VISUALIZATION DASHBOARD                          │
│  • Real-time Metrics • Interactive Charts • Actionable Alerts       │
└─────────────────────────────────────────────────────────────────────┘
```

### 📁 Project Structure

| Module | Purpose | Key Components |
|--------|---------|----------------|
| `data_generator/` | Simulated visitor generation | Humans, AI agents, bots (5 complexity levels) |
| `pipeline/` | Feature engineering | 9-trait behavioral fingerprinting |
| `traffic/` | Visitor classification | ML-based classification, anomaly detection |
| `behaviour/` | User journey analysis | Funnel analysis, next-page prediction |
| `link/` | Cross-analysis | Traffic source ↔ behavior correlation |
| `agent/` | Report generation | Evidence-checked natural language reports |
| `dashboard/` | Visualization | Interactive Streamlit interface |
| `tracker/` | Live data collection | Privacy-safe JavaScript tracker |
| `evaluation/` | Performance scoring | Ground truth validation |

---

## 🎯 Visitor Classification System

### The Four Categories

<table>
<tr>
<td width="25%" align="center">
<h3>👤 Human</h3>
<p>Real person browsing naturally</p>
<p><strong>Characteristics:</strong></p>
<ul align="left">
<li>Variable timing</li>
<li>Mouse movements</li>
<li>Realistic interactions</li>
<li>Session depth variance</li>
</ul>
</td>
<td width="25%" align="center">
<h3>🤖 AI Agent</h3>
<p>Legitimate AI assistant</p>
<p><strong>Characteristics:</strong></p>
<ul align="left">
<li>Systematic browsing</li>
<li>High efficiency</li>
<li>Goal-oriented paths</li>
<li>Often legitimate customers</li>
</ul>
</td>
<td width="25%" align="center">
<h3>🕷️ Bot</h3>
<p>Scraper or malicious script</p>
<p><strong>Characteristics:</strong></p>
<ul align="left">
<li>Rapid page access</li>
<li>Repetitive patterns</li>
<li>No realistic interactions</li>
<li>Suspicious device profiles</li>
</ul>
</td>
<td width="25%" align="center">
<h3>❓ Unknown</h3>
<p>Uncertain classification</p>
<p><strong>Characteristics:</strong></p>
<ul align="left">
<li>Novel behavior patterns</li>
<li>Mixed signals</li>
<li>Zero-day threats</li>
<li>Requires human review</li>
</ul>
</td>
</tr>
</table>

### 🔬 9-Trait Behavioral Fingerprint

| Trait | Measures | Use Case |
|-------|----------|----------|
| **Speed** | Pages per minute | Bots browse 3-10x faster than humans |
| **Focus** | Page type concentration | Bots target specific content systematically |
| **Touch** | Mobile touch interactions | Fake mobile devices never touch screen |
| **Return** | Repeat visits | Humans return, scrapers don't |
| **Depth** | Pages per session | Shallow sessions indicate reconnaissance |
| **Duration** | Time on site | Too fast = bot, too long = abandoned tab |
| **Path Randomness** | Navigation entropy | Humans wander, bots follow patterns |
| **Conversion** | Purchase completion | Real shoppers vs data collectors |
| **Device Consistency** | Device profile validity | Contradictory specs indicate spoofing |

---

## 📊 Performance Metrics

### Classification Accuracy

```
╔════════════════════════════════════════════════════════════╗
║  Visitor Type    │  Precision  │  Recall  │   F1 Score   ║
╠════════════════════════════════════════════════════════════╣
║  Humans          │    97.3%    │  95.8%   │    96.5%     ║
║  AI Agents       │    89.2%    │  91.4%   │    90.3%     ║
║  Bots (Known)    │    94.1%    │  92.7%   │    93.4%     ║
║  Zero-day Bots   │   100.0%    │ (flagged as Unknown)    ║
╠════════════════════════════════════════════════════════════╣
║  Overall         │    92.7%    │  93.2%   │    92.9%     ║
╚════════════════════════════════════════════════════════════╝
```

### Problem Detection Results

**12 Planted Issues → 11 Detected (91.7% success rate)**

<table>
<tr>
<th>Web Traffic Issues</th>
<th>User Behavior Issues</th>
</tr>
<tr>
<td>

✅ Dumb bots (100% detected)  
⚠️ Smart bots (72.7% detected)  
✅ Scraper activity  
✅ Traffic spike anomaly  
✅ Low-quality source identified  
✅ Fake device profiles  

</td>
<td>

✅ Dead-end pages found  
✅ Checkout funnel leak (69.8% → 5.15%)  
✅ Infinite loops detected  
✅ Rage click patterns  
✅ Hidden valuable pages  
✅ Human vs AI behavior gaps  

</td>
</tr>
</table>

### Key Business Impact

- **Conversion Rate Accuracy**: 3.57% (raw) → 5.15% (cleaned) → 4.90% (true human value)
- **False Positive Rate**: 2.7% humans misclassified + 4.2% sent to Unknown = **6.9% total**
- **Bot Traffic Volume**: 45.2% of total visitors
- **AI Agent Traffic**: 12.8% (mostly legitimate shoppers)

---

## 🛡️ AI Report Generation & Validation

### Evidence-Based Insights

TrafficLens generates natural language reports with built-in validation:

✅ **Fact-Checked**: Every statistic is validated against computed data  
✅ **Transparent**: Clearly marks assumptions vs. facts  
✅ **Actionable**: Four-part structure (What, Where, Likely Cause, Fix)  
✅ **Honest**: Says "uncertain" when confidence is low  

### Report Structure

```
📌 Finding: Cart abandonment spike on shipping page
├─ What: 47.3% of users abandon at shipping.html
├─ Where: Payment funnel, step 3 of 4  
├─ Likely Cause: Unexpected shipping costs (⚠️ hypothesis)
└─ Fix: Display shipping estimate earlier in funnel
```

### Safety Guarantees

Run validation checks:
```bash
python -m tests.test_checks
```

**Verified:**
- ✅ Analysis never accesses answer key (blind evaluation)
- ✅ All report numbers traceable to calculations
- ✅ Deterministic results with same random seed
- ✅ No invented statistics

---

## 🔒 Privacy & Ethics

### Privacy-First Design

- **No PII Collection**: No names, emails, or personal identifiers
- **Aggregate Analysis**: All insights from population patterns
- **GDPR Compliant**: Respects Do Not Track signals
- **Transparent Tracking**: Clear disclosure requirements

### Ethical Considerations

⚠️ **Important Limitations:**
- Simulated data may not reflect real-world complexity
- Detection rules calibrated on training data (may need tuning)
- Legitimate AI agents deserve fair treatment as customers
- Manual review recommended for Unknown classifications

📄 **See `report/PRIVACY.md` for full guidelines before production use**

---

## 🛠️ Tech Stack

### Core Technologies
- **Python 3.10+** - Primary language
- **Streamlit** - Interactive dashboard framework
- **Pandas & NumPy** - Data processing
- **NetworkX** - Journey graph analysis
- **Scikit-learn** - Machine learning models

### Analysis Modules
- **Traffic Classification** - Rule-based + ML hybrid approach
- **Behavioral Fingerprinting** - Feature engineering pipeline
- **Anomaly Detection** - Statistical outlier identification
- **Predictive Modeling** - Next-page and conversion prediction

### Visualization
- **Plotly** - Interactive charts
- **Altair** - Statistical visualizations
- **Custom D3.js** - Journey graphs

---

## 📚 Documentation

- **[RESULTS.md](report/RESULTS.md)** - Detailed performance analysis and accuracy tables
- **[AGENT_REPORT.md](report/AGENT_REPORT.md)** - AI-generated findings and recommendations
- **[PRIVACY.md](report/PRIVACY.md)** - Privacy guidelines and ethical considerations
- **[DEPLOY.md](DEPLOY.md)** - Deployment instructions for various platforms

---

## 🤝 Contributing

We welcome contributions! Areas for improvement:

- [ ] Real-world dataset testing
- [ ] Additional ML models for classification
- [ ] Enhanced AI agent differentiation
- [ ] Real-time streaming analytics
- [ ] Mobile app behavior patterns
- [ ] API rate limiting detection

### Development Setup

```bash
# Clone and install
git clone https://github.com/Vigneshreddy99/trafficlens.git
cd trafficlens
pip install -r requirements.txt

# Run tests
python -m pytest tests/

# Run linting
pylint traffic/ behavior/ agent/
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

**Project by:** Vignesh Reddy  
**Contact:** 2320030126@klh.edu.in  
**GitHub:** [@Vigneshreddy99](https://github.com/Vigneshreddy99)

---

## 🙏 Acknowledgments

- Inspired by real-world challenges in e-commerce fraud detection
- Built with modern web analytics best practices
- Designed for transparency and ethical AI usage

---

## ⚠️ Disclaimer

**Important Notes:**

- ✅ **Simulated Data**: All traffic data is synthetically generated for demonstration
- ⚠️ **Research Project**: Requires calibration for production use
- 🔍 **Validation Needed**: Manual review recommended for critical decisions
- 🛡️ **No Warranty**: Provided as-is for educational and research purposes

**Not Covered:**
- Click fraud on ad networks
- Account takeover prevention
- Payment fraud detection
- DDoS attack mitigation
- Server-side log analysis

---

<div align="center">

### 🌟 Star this repository if you find it useful!

[![GitHub stars](https://img.shields.io/github/stars/Vigneshreddy99/trafficlens?style=social)](https://github.com/Vigneshreddy99/trafficlens/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Vigneshreddy99/trafficlens?style=social)](https://github.com/Vigneshreddy99/trafficlens/network/members)

**[⬆ Back to Top](#-trafficlens)**

</div>

---

## 🚀 Deployment

### Streamlit Cloud (Recommended)

1. Push to GitHub (already done!)
2. Visit [Streamlit Cloud](https://streamlit.io/cloud)
3. Connect your repository: `Vigneshreddy99/trafficlens`
4. Set main file: `streamlit_app.py`
5. Deploy!

🌐 **Live Demo**: https://trafficlens-cyrpftkfdrjyprq3wfehz4.streamlit.app/

### Docker Deployment

```bash
# Build image
docker build -t trafficlens .

# Run container
docker run -p 8501:8501 trafficlens
```

### Local Development

```bash
# Development mode with auto-reload
streamlit run streamlit_app.py --server.runOnSave true
```

---

## 📈 Use Cases

### E-Commerce
- Identify bot traffic inflating conversion rates
- Optimize checkout flow based on real human behavior
- Detect price scraping competitors
- Welcome AI shopping assistants (potential customers!)

### Content Publishing
- Distinguish legitimate AI crawlers from scrapers
- Identify engagement patterns for content optimization
- Detect click fraud on ad networks
- Measure true human readership

### SaaS Platforms
- Detect account takeover attempts
- Identify automated testing vs. real users
- Optimize onboarding flows
- Prevent API abuse

### Marketing Analytics
- True attribution modeling (humans only)
- Source quality assessment
- Campaign performance without bot inflation
- A/B test validity

---

## 🔧 Advanced Usage

### Custom Data Analysis

```bash
# Use your own collected data
python tracker/collector.py &
python demo_shop/serve.py

# Visit http://localhost:8000/demo_shop/index.html
# Browse to generate events in data/live/events.jsonl

# Convert and analyze
python -m tracker.live_to_tables
export TRAFFICLENS_DATA=data/live
python run_all.py --skip-generate
```

### Configuration

Edit `config.py` to customize:
- Classification thresholds
- Anomaly detection sensitivity
- Report generation parameters
- Feature engineering options

### API Integration

```python
from traffic.classifier import TrafficClassifier
from pipeline.features import FeatureBuilder

# Load your data
sessions_df = pd.read_csv('your_sessions.csv')
pageviews_df = pd.read_csv('your_pageviews.csv')

# Build features
features = FeatureBuilder(sessions_df, pageviews_df).build()

# Classify visitors
classifier = TrafficClassifier()
predictions = classifier.predict(features)
```
