# Python IDE Setup Guide for Data Science & Machine Learning

This guide provides comprehensive instructions for setting up Python development environments specifically optimized for Data Science and Machine Learning work. We'll cover two primary IDE options:

1. **Visual Studio Code** - A lightweight, extensible code editor that can be transformed into a powerful IDE
2. **PyCharm** - A full-featured Python IDE with built-in tools for data science

---

## 🎯 Quick Start

Choose your preferred IDE:

- **My recommednation**: Start with VS Code, you can expand into a full-blown IDE it as required.
- **For students**: PyCharm Professional is free with GitHub Student Pack. GitHub Coplot extension is also free for students within VS Code (also free limited number of requests per month).

---

## 📋 Prerequisites

Before installing any IDE, ensure you have:

### Python Installation

- **Python 3.8+** (recommended: Python 3.10 or 3.11)
- **Package manager**: pip (comes with Python) or conda

## 🔧 Option 1: Visual Studio Code Setup

Visual Studio Code is a free, open-source editor that becomes a powerful Python IDE with the right extensions.

### Installation

#### Windows

```bash
# Option 1: Download installer
# Visit: https://code.visualstudio.com/download

# Option 2: Using winget
winget install Microsoft.VisualStudioCode

# Option 3: Using Chocolatey
choco install vscode
```

#### macOS

```bash
# Option 1: Download from website
# Visit: https://code.visualstudio.com/download

# Option 2: Using Homebrew
brew install --cask visual-studio-code
```

#### Linux

The easiest way to install Visual Studio Code for Debian/Ubuntu based distributions is to download and install the [.deb package (64-bit)](https://go.microsoft.com/fwlink/?LinkID=760868), either through the graphical software center if it's available, or through the command line with:

```bash
sudo apt install ./<file>.deb
# If you're on an older Linux distribution, you will need to run this instead:
# sudo dpkg -i <file>.deb
# sudo apt-get install -f # Install dependencies
```

When you install the .deb package, it prompts to install the apt repository and signing key to enable auto-updating using the system's package manager.

### Essential Extensions for Data Science & ML

Install these extensions to transform VS Code into a powerful Python data science IDE:

#### Core Python Extensions

```vscode-extensions
ms-python.python,ms-python.vscode-pylance,ms-python.debugpy
```

#### Jupyter & Data Science

```vscode-extensions
ms-toolsai.jupyter,ms-toolsai.jupyter-renderers,ms-toolsai.datawrangler
```

#### Code Quality & Formatting

```vscode-extensions
ms-python.black-formatter,ms-python.isort,charliermarsh.ruff,ms-python.pylint
```

#### AI & Productivity

```vscode-extensions
github.copilot,github.copilot-chat,visualstudioexptteam.vscodeintellicode
```

#### Git & Version Control

```vscode-extensions
eamodio.gitlens,github.vscode-pull-request-github,donjayamanne.githistory
```

#### Themes & Icons

```vscode-extensions
pkief.material-icon-theme,github.github-vscode-theme
```

#### Additional Utilities

```vscode-extensions
formulahendry.code-runner,davidanson.vscode-markdownlint,christian-kohler.path-intellisense
```

### Recommended Keyboard Shortcuts

| Function | Windows/Linux | macOS |
|----------|---------------|-------|
| Run Cell | `Ctrl+Enter` | `Cmd+Enter` |
| Run Cell and Advance | `Shift+Enter` | `Shift+Enter` |
| Command Palette | `Ctrl+Shift+P` | `Cmd+Shift+P` |
| Quick Open | `Ctrl+P` | `Cmd+P` |
| Toggle Terminal | `Ctrl+`` | `Cmd+`` |
| Format Document | `Shift+Alt+F` | `Shift+Option+F` |

---

## 🐍 Option 2: PyCharm Setup

PyCharm is a full-featured Python IDE developed by JetBrains, available in Community (free) and Professional (paid) editions.

### Installation

#### Download Options

- **PyCharm Community** (Free): <https://www.jetbrains.com/pycharm/download/>
- **PyCharm Professional** (Paid): <https://www.jetbrains.com/pycharm/download/>
- **Students**: Free Professional license at <https://www.jetbrains.com/student/>

#### Windows

```bash
# Option 1: Download installer from website
# Visit: https://www.jetbrains.com/pycharm/download/#section=windows

# Option 2: Using winget
winget install JetBrains.PyCharm.Community
# or for Professional
winget install JetBrains.PyCharm.Professional

# Option 3: Using Chocolatey
choco install pycharm-community
# or for Professional
choco install pycharm
```

#### macOS

```bash
# Option 1: Download from website
# Visit: https://www.jetbrains.com/pycharm/download/#section=mac

# Option 2: Using Homebrew
brew install --cask pycharm-ce
# or for Professional
brew install --cask pycharm
```

#### Linux

```bash
# Ubuntu/Debian using Snap
sudo snap install pycharm-community --classic
# or for Professional
sudo snap install pycharm-professional --classic

# Arch Linux
yay -S pycharm-community-edition
# or for Professional
yay -S pycharm-professional

# Flatpak (universal)
flatpak install flathub com.jetbrains.PyCharm-Community
# or for Professional
flatpak install flathub com.jetbrains.PyCharm-Professional
```

### PyCharm Configuration for Data Science

#### Essential Plugins

1. **Data Science Tools** (Professional only):
   - Jupyter Notebook integration
   - R language support
   - Database tools

2. **Community Plugins**:
   - `.ignore` - Git ignore files support
   - `Rainbow Brackets` - Colored bracket matching
   - `Material Theme UI` - Modern themes
   - `Git Toolbox` - Enhanced Git integration

#### Settings Configuration

1. **Python Interpreter Setup**:
   - File → Settings → Project → Python Interpreter
   - Add new environment or select existing one
   - Configure virtual environment path

2. **Code Style**:
   - File → Settings → Editor → Code Style → Python
   - Set line length to 88 (Black formatter standard)
   - Enable auto-formatting on save

3. **Jupyter Integration** (Professional):
   - File → Settings → Languages & Frameworks → Jupyter
   - Configure Jupyter server settings
   - Enable variable explorer

### PyCharm vs VS Code Comparison

| Feature | VS Code | PyCharm Community | PyCharm Professional |
|---------|---------|-------------------|---------------------|
| **Price** | Free | Free | Paid (~$90/year) |
| **Jupyter Support** | Excellent (with extensions) | Basic | Excellent |
| **Database Tools** | Extensions needed | No | Built-in |
| **Scientific Tools** | Extensions needed | Limited | Built-in |
| **Performance** | Fast | Medium | Medium-Slow |
| **Memory Usage** | Low | Medium | High |
| **Learning Curve** | Easy | Medium | Medium |
| **Customization** | Highly customizable | Moderate | Moderate |

---

## 🔍 Troubleshooting

### Common Issues and Solutions

#### Python Interpreter Not Found

- **VS Code**: Use `Ctrl+Shift+P` → "Python: Select Interpreter"
- **PyCharm**: File → Settings → Project → Python Interpreter

#### Jupyter Kernel Issues

```bash
# Reinstall ipykernel
pip install --upgrade ipykernel

# Register kernel
python -m ipykernel install --user --name=my_env
```

#### Import Errors

- Check virtual environment is activated
- Verify package installation: `pip list`
- Check PYTHONPATH in IDE settings

#### Git Integration Issues

- Ensure Git is installed and in PATH
- Configure Git user: `git config --global user.name "Your Name"`
- Configure Git email: `git config --global user.email "your.email@example.com"`

---

## 📚 Additional Resources

### Learning Resources

- **Python.org Tutorial**: <https://docs.python.org/3/tutorial/>
- **Pandas Documentation**: <https://pandas.pydata.org/docs/>
- **Scikit-learn Tutorials**: <https://scikit-learn.org/stable/tutorial/>
- **Jupyter Documentation**: <https://jupyter.readthedocs.io/>

### Community and Support

- **VS Code Python**: <https://github.com/microsoft/vscode-python>
- **PyCharm Support**: <https://www.jetbrains.com/support/pycharm/>
- **Stack Overflow**: <https://stackoverflow.com/questions/tagged/python>
- **Python Discord**: <https://discord.gg/python>

### Useful Tools

- **Python Package Index**: <https://pypi.org/>
- **Anaconda Distribution**: <https://www.anaconda.com/products/distribution>
- **Poetry** (Dependency Management): <https://python-poetry.org/>
- **Pre-commit Hooks**: <https://pre-commit.com/>

---

## ✅ Quick Setup Checklist

- [✅] Python 3.8+ installed
- [✅] IDE installed (VS Code or PyCharm)
- [✅] Essential extensions/plugins installed
- [ ] Project structure created
- [ ] Virtual environment created
- [ ] Git installed and configured
- [ ] venv working correctly
- [ ] Git repository initialized and pushed to GitHub

---

## 🎯 Next Steps

1. **Setup your Virtual Environment** using this guide: [Virtual Environment Setup Guide](../VirtualEnv/README_venv.md)

---

*Happy coding! 🚀*

> **Note**: This guide is regularly updated. For the latest information, check the official documentation of each tool.
