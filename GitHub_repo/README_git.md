# 🔄 Git & GitHub Setup Guide for Data Science Projects

This guide walks you through setting up Git version control and GitHub integration for your data science project. We'll build on the project structure you created in the previous VirtualEnv tutorial.

---

## 📋 Prerequisites

Before starting, ensure you have:

- ✅ Completed the VirtualEnv setup tutorial
- ✅ Your `my_data_project/` directory with the recommended structure
- ✅ Active virtual environment (any of the three workflows: pyenv+venv, conda, or uv)

---

## 🛠️ Step 1: Install and Configure Git

### Installing Git

#### Windows

```bash
# Option 1: Download installer
# Visit: https://git-scm.com/downloads/windows

# Option 2: Using winget
winget install Git.Git

# Option 3: Using Chocolatey
choco install git
```

#### macOS

```bash
# Option 1: Download from website
# Visit: https://git-scm.com/downloads/mac

# Option 2: Using Homebrew (recommended)
brew install git

# Option 3: Using Xcode Command Line Tools
xcode-select --install
```

#### Linux

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install git

# Fedora/RHEL/CentOS
sudo dnf install git

# Arch Linux
sudo pacman -S git
```

### Configure Git

After installation, configure Git with your information:

```bash
# Set your name (replace with your actual name)
git config --global user.name "Your Full Name"

# Set your email (use the same email as your GitHub account)
git config --global user.email "your.email@example.com"

# Set default branch name to 'main'
git config --global init.defaultBranch main

# Verify configuration
git config --list

# Set default editor (optional)
git config --global core.editor "code --wait"  # For VS Code
```

---

## 🐙 Step 2: Set Up GitHub Account

### Create GitHub Account

1. Visit <https://github.com>
2. Click "Sign up" and create your account
3. Verify your email address
4. Complete the setup process

### Configure SSH Authentication (Recommended)

SSH keys provide secure authentication without entering passwords repeatedly.

#### Generate SSH Key

```bash
# Generate SSH key (replace with your GitHub email)
ssh-keygen -t ed25519 -C "your.email@example.com"

# When prompted, press Enter to accept default file location
# Enter a secure passphrase (optional but recommended)

# Start SSH agent
eval "$(ssh-agent -s)"

# Add SSH key to agent
ssh-add ~/.ssh/id_ed25519
```

#### Add SSH Key to GitHub

```bash
# Copy SSH public key to clipboard
# macOS
pbcopy < ~/.ssh/id_ed25519.pub

# Linux (with xclip)
xclip -selection clipboard < ~/.ssh/id_ed25519.pub

# Windows (Git Bash)
clip < ~/.ssh/id_ed25519.pub

# If the above don't work, display and copy manually
cat ~/.ssh/id_ed25519.pub
```

1. Go to GitHub → Settings → SSH and GPG keys
2. Click "New SSH key"
3. Add a descriptive title (e.g., "My Laptop")
4. Paste your public key
5. Click "Add SSH key"

#### Test SSH Connection

```bash
# Test GitHub connection
ssh -T git@github.com

# You should see a message like:
# "Hi username! You've successfully authenticated, but GitHub does not provide shell access."
```

---

## 📁 Step 3: Prepare Your Project Directory

Navigate to your project directory created in the VirtualEnv tutorial:

```bash
# Navigate to your project
cd my_data_project

# Verify your project structure
ls -la

# Should show:
# data/
# notebooks/
# src/
# tests/
# requirements.txt (or environment.yml or pyproject.toml)
# README.md
# .gitignore
```

### Create Enhanced .gitignore

Create or update your `.gitignore` file (if you don't have one yet):

```gitignore
# Virtual Environments
venv/
.venv/
env/
ENV/
ds_env/
.conda/
.uv/

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/

# Jupyter Notebook
.ipynb_checkpoints
*/.ipynb_checkpoints/*

# Data files (consider using Git LFS for large files)
*.csv
*.json
*.xlsx
*.pkl
*.h5
data/raw/
data/processed/
*.parquet

# Model files
models/
*.model
*.joblib

# IDE and Editor files
.vscode/
.idea/
*.swp
*.swo
*~

# OS files
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# Environment variables
.env
.env.local

# Logs
*.log
logs/

# Temporary files
tmp/
temp/
```

---

## 🚀 Step 4: Initialize Git Repository

### Initialize Repository

```bash
# Initialize Git repository
git init

# Check status
git status
```

**Note**: If you used `uv init`, Git repository and `.gitignore` are already created automatically.

### First Commit

```bash
# Add all files to staging area
git add .

# Check what's staged
git status

# Make initial commit
git commit -m "Initial commit: Project structure setup"

# View commit history
git log --oneline
```

---

## 📓 Step 5: Create and Test Jupyter Notebook

Let's create a Jupyter notebook to test our setup:

### Activate Your Environment

```bash
# Activate your environment (choose based on your workflow)

# For pyenv + venv
source venv/bin/activate

# For conda
conda activate ds_env

# For uv
source .venv/bin/activate  # Linux/macOS
# or .venv\Scripts\activate  # Windows
```

### Create Jupyter Notebook

```bash
# Navigate to notebooks directory
cd notebooks

# Create a new notebook (we'll do this in VS Code or directly)
touch hello_world.ipynb

# Go back to project root
cd ..
```

### Create Notebook Content

Create `notebooks/hello_world.ipynb` with the following content:

<VSCode.Cell language="markdown">

# Hello World Data Science Project

This is our first notebook to test the environment setup.
</VSCode.Cell>

<VSCode.Cell language="python">

# Hello World in Python

print("Hello, Data Science World!")
print("🚀 Environment setup successful!")
</VSCode.Cell>

<VSCode.Cell language="python">

# Test numpy import and basic operation

import numpy as np

# Create a simple array

arr = np.array([1, 2, 3, 4, 5])
print(f"Array: {arr}")
print(f"Array mean: {np.mean(arr)}")
print(f"Array sum: {np.sum(arr)}")
print(f"NumPy version: {np.**version**}")
</VSCode.Cell>

<VSCode.Cell language="python">

# Test pandas import

import pandas as pd

# Create a simple DataFrame

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'London', 'Tokyo']
}

df = pd.DataFrame(data)
print("Sample DataFrame:")
print(df)
print(f"\nPandas version: {pd.**version**}")
</VSCode.Cell>

### Run the Notebook

1. Open VS Code in your project directory
2. Open `notebooks/hello_world.ipynb`
3. Select your Python interpreter (the one from your virtual environment)
4. Run each cell and verify everything works

---

## 🐍 Step 6: Create Python Script

Create a Python script to complement our notebook:

```bash
# Create main.py in project root
touch main.py
```

Add the following content to `main.py`:

```python
#!/usr/bin/env python3
"""
Main script for testing the data science environment setup.
"""

import sys
import numpy as np
import pandas as pd


def main():
    """Main function to test our environment."""
    print("=" * 50)
    print("🚀 Data Science Environment Test")
    print("=" * 50)
    
    # Python version
    print(f"Python version: {sys.version}")
    
    # Test NumPy
    print(f"\n📊 NumPy version: {np.__version__}")
    arr = np.random.random(5)
    print(f"Random array: {arr}")
    print(f"Array statistics - Mean: {np.mean(arr):.3f}, Std: {np.std(arr):.3f}")
    
    # Test Pandas
    print(f"\n📈 Pandas version: {pd.__version__}")
    
    # Create sample data
    data = {
        'Product': ['Laptop', 'Mouse', 'Keyboard', 'Monitor'],
        'Price': [999.99, 25.50, 75.00, 299.99],
        'Quantity': [10, 50, 30, 15]
    }
    
    df = pd.DataFrame(data)
    print("\nSample inventory data:")
    print(df)
    
    # Calculate total value
    df['Total_Value'] = df['Price'] * df['Quantity']
    print(f"\nTotal inventory value: ${df['Total_Value'].sum():,.2f}")
    
    print("\n✅ Environment test completed successfully!")


if __name__ == "__main__":
    main()
```

### Test the Script

```bash
# Run the script
python main.py

# You should see output showing Python, NumPy, and Pandas working correctly
```

---

## 📝 Step 7: Commit Your Changes

Now let's commit our new files:

```bash
# Check current status
git status

# Add specific files
git add notebooks/hello_world.ipynb
git add main.py

# Or add all changes
git add .

# Commit with descriptive message
git commit -m "Add: Hello World notebook and main.py test script

- Created hello_world.ipynb with environment tests
- Added main.py with comprehensive environment validation
- Tested NumPy and Pandas functionality"

# View commit history
git log --oneline
```

---

## 🔄 Step 8: Essential Git Commands

### Basic Git Workflow

```bash
# 1. Check status (always start here)
git status

# 2. See what changed
git diff

# 3. Add changes to staging area
git add filename.py           # Add specific file
git add .                     # Add all changes
git add notebooks/            # Add all files in directory

# 4. Commit changes
git commit -m "Descriptive commit message"

# 5. View history
git log                       # Detailed history
git log --oneline            # Compact history
git log --graph --oneline    # Visual branch history
```

### Working with Changes

```bash
# View changes in specific file
git diff filename.py

# View staged changes
git diff --staged

# Unstage a file
git reset filename.py

# Discard changes in working directory (be careful!)
git checkout -- filename.py

# View file at specific commit
git show commit-hash:filename.py
```

### Branch Operations

```bash
# Create and switch to new branch
git checkout -b feature/data-analysis

# Switch between branches
git checkout main
git checkout feature/data-analysis

# List branches
git branch

# Merge branch (from main)
git merge feature/data-analysis

# Delete branch
git branch -d feature/data-analysis
```

---

## 🐙 Step 9: Publish to GitHub

### Create GitHub Repository

1. Go to <https://github.com>
2. Click the "+" icon → "New repository"
3. Repository name: `my-data-project` (or your preferred name)
4. Description: "My first data science project"
5. Choose "Public" or "Private"
6. **Don't** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

### Connect Local Repository to GitHub

```bash
# Add GitHub repository as remote origin
git remote add origin git@github.com:your-username/my-data-project.git

# Verify remote
git remote -v

# Push to GitHub (first time)
git push -u origin main

# For subsequent pushes
git push
```

### Verify on GitHub

1. Refresh your GitHub repository page
2. You should see all your files uploaded
3. Check that the README.md displays properly
4. Verify the notebook renders correctly

---

## 🔄 Step 10: Pull and Push Workflow

### Making Changes and Pushing

```bash
# Make some changes to your files
echo "# Project Updates" >> CHANGELOG.md

# Standard workflow
git status
git add CHANGELOG.md
git commit -m "Add: Project changelog file"
git push
```

### Pulling Changes

```bash
# Pull latest changes from GitHub (important when collaborating)
git pull

# Pull specific branch
git pull origin main

# Fetch changes without merging
git fetch
git merge origin/main
```

### Handling Conflicts

If you encounter merge conflicts:

```bash
# Pull changes
git pull

# Edit conflicted files to resolve conflicts
# Look for conflict markers: <<<<<<< ======= >>>>>>>

# After resolving conflicts
git add conflicted-file.py
git commit -m "Resolve merge conflict in conflicted-file.py"
git push
```

---

## 🎨 Step 11: VS Code GitHub Integration

VS Code provides excellent GitHub integration through built-in features and extensions.

### Built-in Git Features

**Source Control View:**

- Open with `Ctrl+Shift+G` (Windows/Linux) or `Cmd+Shift+G` (macOS)
- View changes, stage files, commit, and push
- See diff of changes inline

**Command Palette Git Commands:**

- `Ctrl+Shift+P` → "Git: Clone"
- `Ctrl+Shift+P` → "Git: Commit"
- `Ctrl+Shift+P` → "Git: Push"
- `Ctrl+Shift+P` → "Git: Pull"

### GitHub Extension Features

The GitHub Pull Requests extension provides:

**Repository Management:**

- Clone repositories directly from VS Code
- Create new repositories on GitHub
- Manage repository settings

**Pull Request Workflow:**

- Create pull requests from VS Code
- Review and merge pull requests
- Comment on code changes
- View PR status and checks

**Issue Integration:**

- View and create GitHub issues
- Link commits to issues
- Close issues with commit messages

### Typical VS Code Workflow

1. **Make Changes**: Edit files in VS Code
2. **View Changes**: Source Control view shows modifications
3. **Stage Changes**: Click "+" next to files or "Stage All Changes"
4. **Commit**: Write commit message and click "Commit"
5. **Push**: Click "Sync Changes" or "Push" button
6. **Create PR**: Use GitHub extension for pull requests

### Useful VS Code Git Shortcuts

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| Source Control | `Ctrl+Shift+G` | `Cmd+Shift+G` |
| Commit | `Ctrl+Enter` | `Cmd+Enter` |
| Stage File | `Ctrl+Enter` | `Cmd+Enter` |
| View Changes | `Ctrl+Shift+D` | `Cmd+Shift+D` |

---

## 🎯 Step 12: Best Practices

### Commit Message Guidelines

**Good commit messages:**

```bash
git commit -m "Add: Data preprocessing pipeline for customer analysis"
git commit -m "Fix: Handle missing values in age column"
git commit -m "Update: Improve model accuracy with feature engineering"
git commit -m "Remove: Deprecated visualization functions"
```

**Commit message format:**

```
Type: Short description (50 chars or less)

Optional longer explanation if needed.
Can include:
- Why this change was made
- What problem it solves
- Any breaking changes
```

**Common types:**

- `Add:` - New features or files
- `Fix:` - Bug fixes
- `Update:` - Improvements to existing features
- `Remove:` - Deleted features or files
- `Docs:` - Documentation changes

### File Organization

```
my_data_project/
├── .git/                    # Git repository data
├── .gitignore              # Git ignore rules
├── README.md               # Project documentation
├── requirements.txt        # Dependencies
├── main.py                 # Main script
├── notebooks/
│   ├── hello_world.ipynb   # Testing notebook
│   └── analysis.ipynb      # Data analysis
├── src/
│   ├── __init__.py
│   ├── data_processing.py  # Data processing functions
│   └── visualization.py    # Plotting functions
├── data/
│   ├── raw/               # Original data (not in git)
│   ├── processed/         # Cleaned data (not in git)
│   └── external/          # Third-party data
└── tests/
    └── test_functions.py   # Unit tests
```

### Collaboration Guidelines

1. **Always pull before pushing**
2. **Use descriptive commit messages**
3. **Keep commits small and focused**
4. **Create branches for features**
5. **Use pull requests for code review**
6. **Don't commit large data files**
7. **Document your code and changes**

---

## ⚡ Quick Reference

### Essential Commands Cheat Sheet

```bash
# Setup
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git init

# Daily workflow
git status                  # Check status
git add .                   # Stage all changes
git commit -m "message"     # Commit changes
git push                    # Push to GitHub
git pull                    # Pull from GitHub

# Repository management
git remote add origin URL   # Connect to GitHub
git push -u origin main     # First push
git clone URL               # Clone repository

# Branching
git checkout -b branch-name # Create and switch branch
git checkout main           # Switch to main
git merge branch-name       # Merge branch
git branch -d branch-name   # Delete branch

# History and inspection
git log --oneline          # View commit history
git diff                   # View changes
git show commit-hash       # View specific commit
```

---

## 🚨 Troubleshooting

### Common Issues and Solutions

**Authentication Failed:**

```bash
# Re-setup SSH key or use personal access token
git remote set-url origin https://github.com/username/repo.git
```

**Large Files Error:**

```bash
# Remove large files from git history
git rm --cached large-file.csv
echo "large-file.csv" >> .gitignore
git add .gitignore
git commit -m "Remove large file and update gitignore"
```

**Merge Conflicts:**

```bash
# Edit conflicted files, then:
git add conflicted-file.py
git commit -m "Resolve merge conflict"
```

**Wrong Commit Message:**

```bash
# Amend last commit message
git commit --amend -m "Corrected message"
```

**Accidentally Committed Wrong Files:**

```bash
# Remove file from last commit
git reset HEAD~1 file-to-remove.py
git commit -m "Remove accidentally committed file"
```

---

## 🎓 Next Steps

Congratulations! You've successfully set up Git version control and GitHub integration for your data science project. You can now:

1. ✅ **Track all changes** to your code and data processing scripts
2. ✅ **Collaborate** with team members on data science projects
3. ✅ **Backup your work** automatically to GitHub
4. ✅ **Share your projects** with the data science community
5. ✅ **Maintain version history** of your experiments and models

### Recommended Learning Path

1. **Practice** the basic workflow daily
2. **Learn branching** for feature development
3. **Explore GitHub Actions** for automation
4. **Try collaborative features** like pull requests
5. **Learn about Git LFS** for large data files
6. **Explore advanced features** like rebasing and cherry-picking

---

## 📚 Additional Resources

### Documentation

- **Git Official**: <https://git-scm.com/doc>
- **GitHub Docs**: <https://docs.github.com/>
- **VS Code Git**: <https://code.visualstudio.com/docs/editor/versioncontrol>

### Learning Resources

- **Git Tutorial**: <https://learngitbranching.js.org/>
- **GitHub Skills**: <https://skills.github.com/>
- **Atlassian Git Tutorial**: <https://www.atlassian.com/git/tutorials>

### VS Code Extensions

- **GitHub Pull Requests**: Manage PRs from VS Code
- **GitLens**: Enhanced Git capabilities
- **Git History**: Visual git log
- **Git Graph**: Interactive git graph

---

## ✅ Quick Setup Checklist

- [✅] Python 3.8+ installed
- [✅] IDE installed (VS Code or PyCharm)
- [✅] Essential extensions/plugins installed
- [✅] Project structure created
- [✅] Virtual environment created
- [✅] Git installed and configured
- [✅] venv working correctly
- [✅] Git repository initialized and pushed to GitHub

---
*🎉 Congratulations on completing the Git and GitHub setup! You're now ready to build amazing data science projects with proper version control! 🚀*
