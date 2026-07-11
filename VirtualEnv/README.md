# 🛠️ Python Virtual Environment Setup Guide

This guide covers three popular workflows for managing Python versions and virtual environments for Data Science and Machine Learning projects. Choose the workflow that best fits your needs and development style.

---

## 🎯 Choose Your Workflow

### 1. **pyenv + pip + venv** (Recommended for most users)

- **Best for**: General Python development, precise version control
- **Pros**: Lightweight, standard Python tools, fine-grained control
- **Cons**: Requires more manual setup, separate dependency management

👉 **[Go to pyenv + pip + venv Workflow Guide](./pip_pyenv/README.md)**

### 2. **conda** (Great for Data Science)

- **Best for**: Data science, scientific computing, complex dependencies
- **Pros**: Built-in package management, handles non-Python dependencies, extensive data science ecosystem
- **Cons**: Larger disk usage, can be slower, package conflicts

👉 **[Go to conda Workflow Guide](./conda/README.md)**

### 3. **uv** (Modern and Fast, My personal recommendation!!)

- **Best for**: Modern Python projects, fast dependency resolution
- **Pros**: Extremely fast, modern tooling, supports both pip and poetry-style workflows
- **Cons**: Newer tool, smaller ecosystem, less documentation

👉 **[Go to uv Workflow Guide](./uv/README.md)**

---

## 📊 Workflow Comparison

| Feature | pyenv + venv | conda | uv |
|---------|--------------|-------|-----|
| **Setup Complexity** | Medium | Easy | Easy |
| **Speed** | Fast | Slow | Very Fast |
| **Disk Usage** | Low | High | Low |
| **Python Version Management** | Excellent | Good | Good |
| **Package Ecosystem** | PyPI | Conda + PyPI | PyPI |
| **Data Science Focus** | Manual | Excellent | Growing |
| **Binary Dependencies** | Manual | Automatic | Manual |
| **Lock Files** | Manual | environment.yml | Manual |
| **Cross-platform** | Good | Excellent | Good |
