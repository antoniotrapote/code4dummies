# GitHub CLI Cheat Sheet

A quick reference guide to the most useful GitHub CLI (`gh`) commands.  
Perfect for daily use directly from the terminal.

---

## 1. Create and Manage Repositories

### 1.1. Step-by-step: Create a new repository from your local folder

```bash
# 1. Initialize a local Git repository
git init

# 2. Stage all files
git add .

# 3. Create the first commit (required before pushing)
git commit -m "Initial commit"
```
### 1.2. Push to a new GitHub repository
```bash
# Create a new GitHub repository and push everything
gh repo create my-new-repo --private --source=. --remote=origin --push
```

#### 🔍 Explanation
| Flag | Description |
|------|--------------|
| `my-new-repo` | Name of the new repository on GitHub. |
| `--private` | Makes the repo private. Use `--public` to make it visible to everyone. |
| `--source=.` | Uses the **current directory** as the source of the new repo. |
| `--remote=origin` | Adds a remote called `origin` pointing to the new GitHub repo. |
| `--push` | Automatically pushes your local commits to GitHub. |

---

#### To make your repo **public**, you can simply run:
  ```bash
  gh repo edit my-repo --visibility public
  ```

---

#### To mark a repo as a **template**, run:
  ```bash
  gh api -X PATCH repos/username/repo-name -f is_template=true
  ```

---
### 1.2. Clone Repositories

```bash
gh repo clone username/repo-name
```

You can also open it directly in VS Code:
```bash
gh repo clone username/repo-name
code repo-name
```

---

### 1.3. Create a new repository from a GitHub template

```bash
# 1. Create a new repository under your account using your template’s structure.
gh repo create new-project-name --template username/project-template --private

# 2. Clone your new project locally (for example, inside ~/Documents/projects/):
cd ~/Documents/projects/
git clone git@github.com:antoniotrapote/new-project-name.git

# 3. Create and activate a new virtual environment
cd new-project-name
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt # (optional)

# 4. Verify that everything is working:
python -c "import sys, os; print('Python:', sys.executable); print('VIRTUAL_ENV:', os.environ.get('VIRTUAL_ENV'))"
```

Expected output:
```
Python: /path/to/new-project-name/.venv/bin/python
VIRTUAL_ENV: /path/to/new-project-name/.venv
```

If both paths match your project folder, your environment is set up correctly ✅

---

### 1.4. Update a repository
```bash
# 1. Check the repository status
git status

# 2. Add files to the staging area
git add .                                  # add all modified files
git add path/to/file1.py path/to/file2.md  # add specific files

# 3. Create a new commit with a descriptive message
git commit -m "Update README with new project link"

# 4. Pull the latest changes from the remote (optional, before pushing)
git pull

# 5. Push local commits to the remote repository
git push
```

---

#### Undo changes
```bash
# Discard local changes in a specific file (before staging)
git checkout -- file.txt

# Remove a file from the staging area (but keep local changes)
git reset file.txt

# Undo the last commit (keep changes in the working directory)
git reset --soft HEAD~1
```
---



## Pull Requests

```bash
# List open PRs
gh pr list

# View details of a PR
gh pr view 23

# Create a new PR
gh pr create --base main --head feature/new-feature --title "Add new feature" --body "Implements new logic"

# Merge a PR (squash and delete branch)
gh pr merge 23 --squash --delete-branch
```

---

## Repository Settings

```bash
# Make a repo public or private
gh repo edit username/my-repo --visibility public \
--accept-visibility-change-consequences 

gh repo edit my-repo --visibility private

# Add a description and topics
gh repo edit my-repo --description "VSCode + Python project template" --add-topic python,vscode,template
```

---

## Releases

```bash
# Create a new release
gh release create v1.0.0 --notes "Initial release"

# Download a release
gh release download v1.0.0
```

---

## Authentication

```bash
# Login (only once per device)
gh auth login

# Check login status
gh auth status

# Logout
gh auth logout
```

---

## Miscellaneous

```bash
# Open a repository in your browser
gh repo view my-repo --web

# List all your repositories
gh repo list antoniotrapote --limit 20

# Delete a repository (be careful!)
gh repo delete my-old-repo
```

---

## Notes

- Always make sure to create an **initial commit** before pushing for the first time.  
- All commands work with **SSH** or **HTTPS** connections.  
- You can use `--help` after any command to see all available options, e.g.:
  ```bash
  gh repo create --help
  ```
- GitHub CLI is fully scriptable, so you can include `gh` commands in automation scripts.

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 
