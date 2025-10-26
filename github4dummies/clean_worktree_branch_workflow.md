# Worktrees and Branches: Clean Workflow in Git
Quick guide to working in an **organized and safe** way with branches and **worktrees** in Git.

---

## 🧩 Key Concepts

| Element | What it does | Where it's created |
|-----------|-----------|---------------|
| **Local branch** | Copy of the history to make isolated changes | Only on your machine |
| **Remote branch** | Copy on GitHub (or another remote) | Only appears after `git push -u origin <branch>` |
| **Worktree** | Additional folder linked to the same repository, to work with another branch without doing checkout | Local |

---

## 🪜 Clean and safe workflow step by step

### 1. Always start from an updated `main`
```bash
cd /path/to/local-repo
git checkout main
git pull origin main
```

---

### 2. Create branch **and** worktree in one step
```bash
git worktree add ../new-folder -b new/branch-name
```

📌 This does:
- Creates the `../new-folder` folder
- Creates a **new local branch** called `new/branch-name` based on the current `main`
- Leaves it **ready to work** inside the new worktree

If the branch already existed locally, omit `-b`:
```bash
git worktree add ../new-folder new/branch-name
```

---

### 3. Enter the worktree and publish the branch to remote
```bash
cd ../new-folder
git status     # should say: On branch new/branch-name
git push -u origin new/branch-name
```

With this:
- The branch **is created on GitHub (remote)**
- The local–remote relationship is configured (upstream)
- You can now do `git push` and `git pull` without arguments

---

## ✅ Checks before working

### View active branch
```bash
git status
# On branch new/branch-name
```

### View relationship with remote
```bash
git branch -vv
# * new/branch-name 1234abc [origin/new/branch-name] Commit message
```

If `detached HEAD` appears, fix it:
```bash
git switch -c new/branch-name
git push -u origin new/branch-name
```

---

## 💾 Work safely

### Normal commit & push
```bash
git add -A # stages all changes
git commit -m "commit message"
git push
```

### Bring changes from `main`
```bash
# update from remote
git fetch origin 

# rebase: replays your commits on top of main
git rebase origin/main 

# merge: creates a merge commit
git merge origin/main

# force-with-lease: safer force push if history was rewritten
git push --force-with-lease
```

---

## 🔀 Create and merge a Pull Request (PR)

```bash
gh pr create -f -t "Pull Request Title" -b "Adds --explanation about the changes"
gh pr merge --squash --delete-branch
```

---

## 🧹 Cleanup when you're done

From the main repo:
```bash
cd /path/to/main-local-repo

# 1. Remove folder and link
git worktree remove ../branch-folder
  
# 2. Delete local branch  
git branch -d new/branch

# 3. Delete remote branch (optional)          
git push origin --delete feat/cli-flags         
```

---

## 🧭 Current state of the repository
Check what worktrees exist:
```bash
git worktree list
```

Correct example:
```
/Users/username/Documents/Folder/main-local-repo  1234abc [main]
/Users/username/Documents/Folder/local-worktree  5678def [feat/cli-flags]
```

---

## ✅ Quick Summary
| Action | Command |
|--------|----------|
| Update main | `git pull origin main` |
| Create branch + worktree | `git worktree add ../folder -b feat/name` |
| Publish branch to remote | `git push -u origin feat/name` |
| View active branch | `git status` |
| Make commit | `git add -A && git commit -m "..."` |
| Push changes | `git push` |
| Merge PR | `gh pr merge --squash --delete-branch` |
| Delete worktree | `git worktree remove ../folder` |
| Delete local/remote branches | `git branch -d feat/name && git push origin --delete feat/name` |

---

## ⚙️ Extra tip

Open **each worktree in a separate VSCode window** with its own `.venv`, to avoid dependency or path conflicts.

---

**Mental workflow summary:**
```
main (stable)
│
└── feat/cli-flags  ← (separate worktree)
      ↓ commit / push
      ↓ PR / merge
      ↓ delete worktree and branch
```

---
CC-BY-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 