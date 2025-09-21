# Installing Python

**Windows:**

```bash
# Option 1: Download from python.org
# Visit: https://www.python.org/downloads/windows/

# Option 2: Using winget
winget install Python.Python.3.11

# Option 3: Using Chocolatey
choco install python311
```

**macOS:**

```bash
# Option 1: Download from python.org
# Visit: https://www.python.org/downloads/macos/

# Option 2: Using Homebrew (recommended)
brew install python@3.11

# Option 3: Using pyenv (for version management)
brew install pyenv
pyenv install 3.11.0
pyenv global 3.11.0
```

**Linux (Ubuntu/Debian):**

```bash
# Update package list
sudo apt update

# Install Python 3.11
sudo apt install python3.11 python3.11-pip python3.11-venv

# Set as default (optional)
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 1
```

## ✅ Quick Setup Checklist

- ✅ Python 3.8+ installed
- [ ] IDE installed (VS Code or PyCharm)
- [ ] Essential extensions/plugins installed
- [ ] Project structure created
- [ ] Virtual environment created
- [ ] Git installed and configured
- [ ] venv working correctly
- [ ] Git repository initialized and pushed to GitHub

## 🎯 Next Steps

1. **Setup your IDE** using this guide: [IDE Setup Guide](../IDE/README.md)
