# 🛠️ Python Virtual Environment Setup Guide

This guide covers three popular workflows for managing Python versions and virtual environments for Data Science and Machine Learning projects. Choose the workflow that best fits your needs and development style.

---

## 🎯 Choose Your Workflow

### 1. **pyenv + pip + venv** (Recommended for most users)

- **Best for**: General Python development, precise version control
- **Pros**: Lightweight, standard Python tools, fine-grained control
- **Cons**: Requires more manual setup, separate dependency management

### 2. **conda** (Great for Data Science)

- **Best for**: Data science, scientific computing, complex dependencies
- **Pros**: Built-in package management, handles non-Python dependencies, extensive data science ecosystem
- **Cons**: Larger disk usage, can be slower, package conflicts

### 3. **uv** (Modern and Fast, My personal recommendation!!)

- **Best for**: Modern Python projects, fast dependency resolution
- **Pros**: Extremely fast, modern tooling, supports both pip and poetry-style workflows
- **Cons**: Newer tool, smaller ecosystem, less documentation

---

## 🚀 Installation Instructions

### Option 1: pyenv + pip + venv Setup

#### Installing pyenv

**macOS:**

```bash
# Using Homebrew (recommended)
brew install pyenv

# Add to shell profile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc

# Reload shell
exec "$SHELL"
```

**Linux (Ubuntu/Debian):**

```bash
# Install dependencies
sudo apt update
sudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl

# Install pyenv
curl https://pyenv.run | bash

# Add to shell profile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc

# Reload shell
exec "$SHELL"
```

**Windows:**

```powershell
# Install using git (requires Git for Windows)
git clone https://github.com/pyenv-win/pyenv-win.git %USERPROFILE%\.pyenv

# Add to environment variables manually or use PowerShell
[Environment]::SetEnvironmentVariable("PYENV", "$env:USERPROFILE\.pyenv\pyenv-win", "User")
[Environment]::SetEnvironmentVariable("PATH", "$env:PATH;$env:USERPROFILE\.pyenv\pyenv-win\bin;$env:USERPROFILE\.pyenv\pyenv-win\shims", "User")
```

### Option 2: conda Setup

#### Installing Miniconda (Lightweight)

**All Platforms:**

```bash
# Download and install Miniconda
# Visit: https://docs.conda.io/en/latest/miniconda.html

# macOS (using Homebrew)
brew install miniconda

# Linux
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh

# Windows: Download installer from website
```

#### Installing Anaconda (Full Distribution)

**All Platforms:**

- Download from: <https://www.anaconda.com/products/distribution>
- Follow platform-specific installation instructions

### Option 3: uv Setup

#### Installing uv

**macOS/Linux:**

```bash
# Install using curl
curl -LsSf https://astral.sh/uv/install.sh | sh

# Or using Homebrew (macOS)
brew install uv

# Or using pip
pip install uv
```

**Windows:**

```powershell
# Install using PowerShell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# Or using pip
pip install uv
```

---

## 🔧 Workflow 1: pyenv + pip + venv

### Step 1: Install and Set Python Version (pyenv)

```bash
# List available Python versions
pyenv install --list

# Install specific Python version
pyenv install 3.11.9

# Set global Python version
pyenv global 3.11.9

# Set local Python version for project
pyenv local 3.11.9

# Verify Python version
python --version
```

### Step 2: Create Virtual Environment (venv)

```bash
# Create virtual environment
python -m venv ds_env

# Activate (Windows)
ds_env\Scripts\activate

# Activate (macOS/Linux)
source ds_env/bin/activate

# Verify activation
which python
```

### Step 3: Install Dependencies (pip)

```bash
# Upgrade pip
pip install --upgrade pip

# Install from requirements.txt
pip install -r requirements.txt

# Or install packages individually
pip install numpy pandas matplotlib scikit-learn

# Generate requirements.txt
pip freeze > requirements.txt
```

### Step 4: Deactivate

```bash
deactivate
```

---

## 🔧 Workflow 2: conda

### Step 1: Create Environment with Specific Python Version

```bash
# Create environment with Python version
conda create -n ds_env python=3.11

# Create with initial packages
conda create -n ds_env python=3.11 numpy pandas matplotlib

# List environments
conda env list
```

### Step 2: Activate Environment

```bash
# Activate
conda activate ds_env

# Verify activation
conda info --envs
which python
```

### Step 3: Install Dependencies

```bash
# Install from conda-forge (recommended)
conda install -c conda-forge numpy pandas matplotlib scikit-learn

# Install from requirements.txt
pip install -r requirements.txt

# Mix conda and pip (install conda packages first)
conda install -c conda-forge numpy pandas
pip install specific-package

# Export environment
conda env export > environment.yml

# Create environment from file
conda env create -f environment.yml
```

### Step 4: Deactivate

```bash
conda deactivate
```

---

## 🔧 Workflow 3: uv

### Step 1: Initialize Project

```bash
# Initialize new project
uv init my_project
cd my_project

# Or initialize in existing directory
uv init
```

### Step 2: Create Virtual Environment

```bash
# Intiialize uv in the project directory. This will create a .uv directory with .git .gitignore and other config files
uv init

# Create environment with specific Python version. The name will be the name of the folder by default
uv venv --python 3.11

# Create with custom name
uv venv ds_env --python 3.11

# Activate (Linux/macOS)
source .venv/bin/activate

# Alternate way to activate
uv sync

# Activate (Windows)
.venv\Scripts\activate
```

### Step 3: Install Dependencies

#### Using requirements.txt (Traditional)

```bash
# Install from requirements.txt
uv pip install -r requirements.txt

# or 
uv add -r requirements.txt

# Install individual packages
uv pip install numpy pandas matplotlib

# or using uv add (adds them to pyproject.toml automatically)
uv add numpy pandas matplotlib

# Generate requirements.txt
uv pip freeze > requirements.txt
```

#### Using pyproject.toml (Modern)

Create a `pyproject.toml` file (automatically gets created when you run `uv init`):

```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "my-data-project"
version = "0.1.0"
description = "A data science project"
authors = [
    { name = "Your Name", email = "your.email@example.com" }
]
dependencies = [
    "numpy>=1.24.0",
    "pandas>=2.0.0",
    "matplotlib>=3.7.0",
    "seaborn>=0.12.0",
    "scikit-learn>=1.3.0",
    "jupyter>=1.0.0",
]

[project.optional-dependencies]
dev = [
    "black>=23.0.0",
    "isort>=5.12.0",
    "flake8>=6.0.0",
    "pytest>=7.4.0",
]
ml = [
    "torch>=2.0.0",
    "tensorflow>=2.13.0",
    "xgboost>=1.7.0",
]

[tool.black]
line-length = 88

[tool.isort]
profile = "black"
```

Install dependencies with uv pip:

```bash
# Install main dependencies
uv pip install -e .

# Install with optional dependencies
uv pip install -e ".[dev]"
uv pip install -e ".[ml]"
uv pip install -e ".[dev,ml]"
```

or with uv add:

```bash
# Install main dependencies
uv add .
# Install with optional dependencies
uv add ".[dev]"
uv add ".[ml]"
uv add ".[dev,ml]"
```

#### Hybrid Approach (Best of Both Worlds)

You can use both `requirements.txt` and `pyproject.toml` together for maximum compatibility:

1. **Use `pyproject.toml`** for project metadata and development
2. **Generate `requirements.txt`** for CI/CD and compatibility

```bash
# Generate requirements.txt from pyproject.toml
uv pip install -e .
uv pip freeze > requirements.txt

# Install from requirements.txt in CI/CD
uv pip install -r requirements.txt
```

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

---

## 📋 Essential Python Packages for Data Science

### Core requirements.txt

```txt
# Core Data Science Stack
numpy>=1.24.0
pandas>=2.0.0
matplotlib>=3.7.0
seaborn>=0.12.0
plotly>=5.14.0
scipy>=1.10.0

# Machine Learning
scikit-learn>=1.3.0
xgboost>=1.7.0
lightgbm>=3.3.0
catboost>=1.2.0

# Deep Learning
torch>=2.0.0
tensorflow>=2.13.0
keras>=2.13.0

# Jupyter and Interactive Development
jupyter>=1.0.0
jupyterlab>=4.0.0
ipywidgets>=8.0.0
ipykernel>=6.25.0

# Data Visualization
bokeh>=3.2.0
altair>=5.0.0

# Data Processing
openpyxl>=3.1.0
xlsxwriter>=3.1.0
requests>=2.31.0
beautifulsoup4>=4.12.0

# Development Tools
black>=23.0.0
isort>=5.12.0
flake8>=6.0.0
pytest>=7.4.0
```

### Conda environment.yml

```yaml
name: ds_env
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.11
  - numpy>=1.24.0
  - pandas>=2.0.0
  - matplotlib>=3.7.0
  - seaborn>=0.12.0
  - scikit-learn>=1.3.0
  - jupyter>=1.0.0
  - jupyterlab>=4.0.0
  - pip
  - pip:
    - plotly>=5.14.0
    - xgboost>=1.7.0
    - lightgbm>=3.3.0
```

---

## 🎓 Getting Started with Your First Project

### 1. Choose Your Workflow

Pick one of the three workflows based on your needs:

- **New to Python**: Start with conda
- **Want control**: Use pyenv + venv
- **Want speed**: Try uv (my personal recommendation!!)

### 2. Create Project Structure

uv init will create a basic structure for you. Here’s a recommended layout:

```
my_data_project/
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── notebooks/
├── src/
│   └── __init__.py
├── tests/
├── requirements.txt      # For pip-based workflows
├── environment.yml       # For conda
├── pyproject.toml       # For uv/modern Python
├── README.md
└── .gitignore
```

### 3. Initialize Your Environment

**pyenv + venv:**

```bash
cd my_data_project
pyenv local 3.11.9
python -m venv venv
source venv/bin/activate  # Linux/macOS
pip install -r requirements.txt
```

**conda:**

```bash
cd my_data_project
conda env create -f environment.yml
conda activate ds_env
```

**uv:**

```bash
cd my_data_project
uv init
uv venv --python 3.11
source .venv/bin/activate  # Linux/macOS
uv add -r requirements.txt
# or
uv sync
```

### 4. Install Jupyter Kernel

```bash
# For all workflows
pip install ipykernel
python -m ipykernel install --user --name=ds_env --display-name="DS Environment"
```

### 5. Start Developing

```bash
# Start Jupyter Lab
jupyter lab

# Or open in your IDE
code .
```

---

## 🚨 Troubleshooting

### Common Issues

**pyenv Python not found:**

```bash
# Rebuild pyenv database
pyenv rehash

# Check available versions
pyenv versions

# Install missing version
pyenv install 3.11.9
```

**Conda environment activation fails:**

```bash
# Initialize conda
conda init

# Restart terminal
exec "$SHELL"
```

**uv installation issues:**

```bash
# Update uv
uv self update

# Clear cache
uv cache clean
```

**Jupyter kernel not found:**

```bash
# List kernels
jupyter kernelspec list

# Remove old kernel
jupyter kernelspec remove old_env_name

# Install new kernel
python -m ipykernel install --user --name=new_env_name
```

---

## 📚 Additional Resources

### Documentation

- **pyenv**: <https://github.com/pyenv/pyenv>
- **conda**: <https://docs.conda.io/>
- **uv**: <https://docs.astral.sh/uv/>
- **pip**: <https://pip.pypa.io/>

### Package Repositories

- **PyPI**: <https://pypi.org/>
- **conda-forge**: <https://conda-forge.org/>
- **Anaconda**: <https://anaconda.org/>

---

## ✅ Quick Setup Checklist

- [✅] Python 3.8+ installed
- [✅] IDE installed (VS Code or PyCharm)
- [✅] Essential extensions/plugins installed
- [✅] Project structure created
- [✅] Virtual environment created
- [ ] Git installed and configured
- [ ] venv working correctly
- [ ] Git repository initialized and pushed to GitHub

---

## 🎯 Next Steps

1. **Setup your first git repo** using this guide: [Git Setup Guide](../GitHub_repo/README.md)

*Choose the workflow that fits your project needs and development style! 🚀*
