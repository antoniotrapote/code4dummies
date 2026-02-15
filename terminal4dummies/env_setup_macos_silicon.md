# Environment Setup for macOS (Clean & Professional)

This guide documents a clean, reproducible, and professional environment setup for macOS,
focused on development and data science workflows.

Tested on:
- macOS Sequoia (tested on 15.x)
- MacBook Pro Silicon (M4)

---

## 0. Install Xcode Command Line Tools

Before installing any software, install the Xcode Command Line Tools.
They include essential development tools required by Homebrew, Python packages,
and many system libraries.

Open Terminal and run:

```bash
xcode-select --install
```

Follow the on-screen instructions to complete the installation.

Verify:

```bash
xcode-select -p
```

Expected output:
```
/Library/Developer/CommandLineTools
```

---

## 1. Install Homebrew

Homebrew is the package manager used to install and manage software on macOS.

Install it by running:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the instructions shown during the installation.

Verify installation:

```bash
brew --version
```

---

## 2. Install Git

Install Git using Homebrew:

```bash
brew install git
```

Verify:

```bash
git --version
```

Optional check to confirm Homebrew Git is used:

```bash
which git
```

Expected path:
```
/opt/homebrew/bin/git
```

### Configure Git

Set your global Git identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@mail.com"
git config --global core.autocrlf input
```
> *autocrlf input ensures consistent line endings across different OSes when collaborating.*

Verify configuration:
```bash
git config --global --list
```

---

## 3. Install Python (Homebrew-managed)

Install a specific Python version via Homebrew.
Pinning the version ensures reproducibility and stability.
```bash
brew install python@3.14
```

Verify:
```bash
python3.14 --version
```

---

## 4. Configure Python PATH (zsh)

Ensure the Homebrew Python version is preferred over the system Python.

Append the following lines to `~/.zshrc`:

```bash
cat <<'EOF' >> ~/.zshrc

# Homebrew Python (preferred)
export PATH="$(brew --prefix)/opt/python@3.14/libexec/bin:$PATH"
EOF
```

Reload the shell configuration:

```bash
source ~/.zshrc
```

Verify:

```bash
which python
python --version
which python3
python3 --version
```

Both should point to the Homebrew Python installation.

Expected output:
```
/opt/homebrew/opt/python@3.14/libexec/bin/python
Python 3.14.x
/opt/homebrew/bin/python3
Python 3.14.x
```

> *Note: The system Python (`/usr/bin/python3`) remains untouched.*

---

## 5. Secure pip (Require Virtual Environments)

To avoid accidentally installing Python packages globally,
configure pip to require an active virtual environment.

```bash
python -m pip config set global.require-virtualenv true
```

Verify:

```bash
python -m pip config list
```

Expected output:
```
global.require-virtualenv = true
```

Test (outside a virtual environment):
```bash
pip install requests
```
This should fail with a message indicating that a virtual environment is required.

---

## 6. Install Visual Studio Code (optional)

Install Visual Studio Code using Homebrew:
```bash
brew install --cask visual-studio-code
```

Launch it:
```bash
open -a "Visual Studio Code"
```

### Enable `code` Command

In VS Code:
1. Press `Cmd + Shift + P`
2. Type: `Shell Command: Install 'code' command in PATH`
3. Confirm installation

Verify:
```bash
code .
```

---

### Set VS Code as Git Editor

Configure Git to use VS Code for commit messages:
```bash
git config --global core.editor "code --wait"
```

Verify:
```bash
git config --global --edit
```

---

## 7. (Optional) Terminal Customization

You may customize your terminal prompt by editing `~/.zshrc`.

Example minimal prompt:

```bash
cat <<'EOF' >> ~/.zshrc

# Custom terminal prompt
PROMPT='%F{green}%1~ ▶ %f'
EOF
```

Reload configuration:

```bash
source ~/.zshrc
```

---

## Recommended Workflow

- One virtual environment per project:
  ```bash
  python -m venv .venv
  source .venv/bin/activate
  ```

- Never install Python packages globally
- Keep Homebrew, Python, and projects clearly separated
- Favor reproducibility over convenience

---

## Philosophy

> The system should stay boring.  
> All complexity belongs inside isolated projects.

This setup prioritizes clarity, stability, and long-term maintainability.

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 