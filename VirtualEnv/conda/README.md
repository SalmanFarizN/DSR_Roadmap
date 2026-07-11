# 🔧 conda Workflow

This guide details the installation, workflow steps, project setup, and troubleshooting for the **conda** Python development workflow.

---

## 🚀 Installation Instructions

### Installing Miniconda (Lightweight)

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

### Installing Anaconda (Full Distribution)

**All Platforms:**

- Download from: <https://www.anaconda.com/products/distribution>
- Follow platform-specific installation instructions

---

## 🔧 Step-by-Step Workflow & Project Setup

### Step 1: Create Project Structure
Initialize a project folder with a directory structure (e.g. data, notebooks, src, tests) and an `environment.yml` file (see the [Essential Packages](#-essential-python-packages-for-data-science) section for a starter template).

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
├── environment.yml       # For conda
├── README.md
└── .gitignore
```

### Step 2: Create Environment with Specific Python Version
You can create a conda environment from scratch or initialize it using your `environment.yml` file:

**Option A: Create environment from scratch:**
```bash
# Create environment with Python version
conda create -n ds_env python=3.11

# Create with initial packages
conda create -n ds_env python=3.11 numpy pandas matplotlib

# List environments
conda env list
```

**Option B: Create environment from `environment.yml`:**
```bash
conda env create -f environment.yml
```

### Step 3: Activate Environment
```bash
# Activate
conda activate ds_env

# Verify activation
conda info --envs
which python
```

### Step 4: Install Dependencies
```bash
# Install from conda-forge (recommended)
conda install -c conda-forge numpy pandas matplotlib scikit-learn

# Install from requirements.txt (if using pip packages inside Conda)
pip install -r requirements.txt

# Mix conda and pip (install conda packages first)
conda install -c conda-forge numpy pandas
pip install specific-package

# Export environment to update environment.yml
conda env export > environment.yml
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
conda deactivate
```

---

## 📋 Essential Python Packages for Data Science

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

## 🚨 Troubleshooting

### Common Issues

**Conda environment activation fails:**

```bash
# Initialize conda
conda init

# Restart terminal
exec "$SHELL"
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

- **conda**: <https://docs.conda.io/>

### Package Repositories

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

1. **Setup your first git repo** using this guide: [Git Setup Guide](../../GitHub_repo/README.md)
