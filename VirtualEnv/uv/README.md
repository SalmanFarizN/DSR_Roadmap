# 🔧 uv Workflow

This guide details the installation, workflow steps, project setup, and troubleshooting for the **uv** Python development workflow.

---

## 🚀 Installation Instructions

### Installing uv

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

## 🔧 Step-by-Step Workflow & Project Setup

### Step 1: Create Project Structure & Initialize Project
You can initialize a project directly with `uv init`:
```bash
# Initialize new project folder
uv init my_project
cd my_project

# Or initialize in an existing directory
uv init
```
This automatically creates a basic folder structure, including a `pyproject.toml` file. A recommended data science layout to build out is:

```
my_project/
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── notebooks/
├── src/
│   └── __init__.py
├── tests/
├── pyproject.toml       # For uv/modern Python
├── README.md
└── .gitignore
```

### Step 2: Create & Activate Virtual Environment
```bash
# Create environment with specific Python version. The name will be '.venv' by default
uv venv --python 3.11

# Create with custom name
uv venv ds_env --python 3.11

# Activate (Linux/macOS)
source .venv/bin/activate

# Activate (Windows)
.venv\Scripts\activate
```

### Step 3: Install Dependencies

#### Approach A: Using requirements.txt (Traditional)
```bash
# Install from requirements.txt
uv pip install -r requirements.txt
# or
uv add -r requirements.txt

# Install individual packages
uv pip install numpy pandas matplotlib
# or (adds them to pyproject.toml automatically)
uv add numpy pandas matplotlib

# Generate requirements.txt
uv pip freeze > requirements.txt
```

#### Approach B: Using pyproject.toml (Modern)
Create or edit your `pyproject.toml` file (e.g. using the template in the [Essential Packages](#-essential-python-packages-for-data-science) section).
Install dependencies with `uv pip`:
```bash
# Install main dependencies
uv pip install -e .

# Install with optional dependencies
uv pip install -e ".[dev]"
uv pip install -e ".[ml]"
uv pip install -e ".[dev,ml]"
```
Or with `uv add` / `uv sync`:
```bash
# Install main dependencies
uv add .

# Install with optional dependencies
uv add ".[dev]"
uv add ".[ml]"
uv add ".[dev,ml]"

# Alternately, sync dependencies from pyproject.toml
uv sync
```

#### Approach C: Hybrid Approach (Best of Both Worlds)
You can use both `requirements.txt` and `pyproject.toml` together for maximum compatibility:
1. **Use `pyproject.toml`** for project metadata and development.
2. **Generate `requirements.txt`** for CI/CD and compatibility.
```bash
# Generate requirements.txt from pyproject.toml
uv pip install -e .
uv pip freeze > requirements.txt

# Install from requirements.txt in CI/CD
uv pip install -r requirements.txt
```

### Step 4: Install Jupyter Kernel (Optional)
If you are working with Jupyter Notebooks/Lab:
```bash
uv add ipykernel
python -m ipykernel install --user --name=ds_env --display-name="DS Environment"
```

### Step 5: Start Developing
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

- **uv**: <https://docs.astral.sh/uv/>

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
