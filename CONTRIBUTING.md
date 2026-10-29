# Contributing to TrafficLens

Thank you for your interest in contributing to TrafficLens! This document provides guidelines and instructions for contributing.

## 🎯 Ways to Contribute

### Code Contributions
- Bug fixes
- New features
- Performance improvements
- Test coverage
- Documentation updates

### Non-Code Contributions
- Report bugs and issues
- Suggest new features
- Improve documentation
- Share use cases and results
- Write tutorials or blog posts

## 🚀 Getting Started

### 1. Fork and Clone

```bash
# Fork the repository on GitHub
# Then clone your fork
git clone https://github.com/YOUR_USERNAME/trafficlens.git
cd trafficlens
```

### 2. Set Up Development Environment

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies
pip install pytest pylint black isort
```

### 3. Create a Branch

```bash
# Create a feature branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/bug-description
```

## 💻 Development Workflow

### Code Style

We follow PEP 8 guidelines with these tools:

```bash
# Format code
black .

# Sort imports
isort .

# Lint code
pylint traffic/ behavior/ agent/ pipeline/
```

### Testing

```bash
# Run all tests
python -m pytest tests/

# Run specific test file
python -m pytest tests/test_checks.py

# Run with coverage
python -m pytest --cov=. tests/
```

### Making Changes

1. **Write clear, focused commits**
   ```bash
   git commit -m "feat: add new anomaly detection algorithm"
   git commit -m "fix: correct conversion rate calculation"
   git commit -m "docs: update API usage examples"
   ```

2. **Follow commit message conventions**
   - `feat:` New feature
   - `fix:` Bug fix
   - `docs:` Documentation changes
   - `test:` Test additions/changes
   - `refactor:` Code refactoring
   - `perf:` Performance improvements
   - `style:` Code style changes
   - `chore:` Build/tooling changes

3. **Keep PRs focused**
   - One feature/fix per PR
   - Include tests for new features
   - Update documentation as needed

## 📝 Pull Request Process

### Before Submitting

- [ ] Code follows style guidelines
- [ ] All tests pass
- [ ] New tests added for new features
- [ ] Documentation updated
- [ ] No merge conflicts with main branch

### Submitting

1. Push to your fork
   ```bash
   git push origin feature/your-feature-name
   ```

2. Create a Pull Request on GitHub
   - Use a clear, descriptive title
   - Describe what changed and why
   - Reference related issues (e.g., "Fixes #123")
   - Add screenshots for UI changes

3. Wait for review
   - Address feedback promptly
   - Make requested changes
   - Keep the discussion constructive

### PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
How has this been tested?

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-reviewed code
- [ ] Commented complex code
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests pass
```

## 🐛 Bug Reports

When reporting bugs, include:

1. **Description**: Clear summary of the bug
2. **Steps to Reproduce**: Numbered steps to trigger the bug
3. **Expected Behavior**: What should happen
4. **Actual Behavior**: What actually happens
5. **Environment**:
   - OS and version
   - Python version
   - TrafficLens version
6. **Additional Context**: Screenshots, logs, etc.

### Bug Report Template

```markdown
**Describe the Bug**
Clear description

**To Reproduce**
1. Step one
2. Step two
3. See error

**Expected Behavior**
What should happen

**Screenshots**
If applicable

**Environment**
- OS: [e.g., Windows 11]
- Python: [e.g., 3.10.5]
- TrafficLens: [e.g., 1.0.0]

**Additional Context**
Any other relevant information
```

## 💡 Feature Requests

When requesting features, include:

1. **Problem**: What problem does this solve?
2. **Proposed Solution**: How should it work?
3. **Alternatives**: Other approaches you've considered
4. **Use Case**: Real-world scenario
5. **Priority**: How important is this?

## 🔍 Code Review

### As a Reviewer

- Be respectful and constructive
- Explain reasoning behind suggestions
- Approve when changes look good
- Point out both positives and areas for improvement

### As an Author

- Don't take feedback personally
- Ask questions if unclear
- Make requested changes promptly
- Thank reviewers for their time

## 📚 Documentation

Good documentation includes:

- Clear explanations
- Code examples
- Expected inputs/outputs
- Edge cases and limitations
- Links to related topics

Update these files as needed:
- `README.md` - Overview and quick start
- `DEPLOY.md` - Deployment instructions
- `report/RESULTS.md` - Performance metrics
- Inline code comments - Complex logic

## 🎨 Design Principles

When contributing, keep these in mind:

1. **Privacy First**: Never collect PII without explicit consent
2. **Transparency**: Make assumptions clear, mark guesses
3. **Accuracy**: Validate all statistics
4. **Performance**: Consider scalability
5. **Usability**: Keep interfaces intuitive
6. **Ethical**: Treat AI agents fairly as potential customers

## 🏆 Recognition

Contributors will be:
- Listed in CONTRIBUTORS.md
- Mentioned in release notes
- Credited in commit history

## ❓ Questions?

- Open a GitHub issue
- Email: 2320030126@klh.edu.in
- Start a discussion in GitHub Discussions

## 📜 Code of Conduct

### Our Pledge

We pledge to make participation in our project a harassment-free experience for everyone.

### Our Standards

**Positive behavior:**
- Using welcoming and inclusive language
- Being respectful of differing viewpoints
- Gracefully accepting constructive criticism
- Focusing on what's best for the community
- Showing empathy towards others

**Unacceptable behavior:**
- Harassment, trolling, or insulting comments
- Personal or political attacks
- Public or private harassment
- Publishing others' private information
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Report unacceptable behavior to: 2320030126@klh.edu.in

## 🙏 Thank You!

Your contributions make TrafficLens better for everyone. Whether it's code, documentation, bug reports, or ideas—every contribution matters!

---

**Happy Contributing! 🚀**
