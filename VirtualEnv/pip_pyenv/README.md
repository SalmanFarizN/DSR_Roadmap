# 🔧 pyenv + pip + venv Workflow

This guide details the installation, workflow steps, project setup, and troubleshooting for the **pyenv + pip + venv** Python development workflow.

---

## 🚀 Installation Instructions

### Installing pyenv

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

---

## 🔧 Step-by-Step Workflow & Project Setup

### Step 1: Create Project Structure
Initialize a project folder with a directory structure (e.g. data, notebooks, src, tests) and a `requirements.txt` file (see the [Essential Packages](#-essential-python-packages-for-data-science) section for a starter template).

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
├── README.md
└── .gitignore
```

### Step 2: Set Python Version (pyenv)
Run the following from your project root to specify which Python version to use:
```bash
# List available Python versions
pyenv install --list

# Install specific Python version
pyenv install 3.11.9

# Set local Python version for your project
pyenv local 3.11.9

# Verify Python version
python --version
```
Note: You can also set a global default version with `pyenv global 3.11.9`.

### Step 3: Create & Activate Virtual Environment (venv)
```bash
# Create virtual environment (e.g. named 'venv' or 'ds_env')
python -m venv venv

# Activate (macOS/Linux)
source venv/bin/activate

# Activate (Windows)
venv\Scripts\activate

# Verify activation
which python
```

### Step 4: Install Dependencies (pip)
Upgrade package installer and install from requirements file:
```bash
# Upgrade pip
pip install --upgrade pip

# Install from requirements.txt
pip install -r requirements.txt

# Or install packages individually
pip install numpy pandas matplotlib scikit-learn

# Generate requirements.txt when you install new packages
pip freeze > requirements.txt
```

### Step 5: Install Jupyter Kernel (Optional)
If you are working with Jupyter Notebooks/Lab:
```bash
pip install ipykernel
python -m ipykernel install --user --name=ds_env --display-name="DS Environment"
```

### Step 6: Start Developing
```bash
# Start Jupyter Lab
jupyter lab

# Or open in your IDE
code .
```

To exit the environment when you are done, run:
```bash
deactivate
```

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
- **pip**: <https://pip.pypa.io/>

### Package Repositories

- **PyPI**: <https://pypi.org/>

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

1. **Setup your first git repo** using this guide: [Git Setup Guide](../../GitHub_repo/README.md)
