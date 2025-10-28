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
git worktree add ../worktree -b new/branch-name
```
📌 This does:
- Creates the `../worktree` folder
- `-b` :Creates a **new local branch** called `new/branch-name` based on the current `main`
- Leaves it **ready to work** inside the new worktree

If the branch already existed locally, omit `-b`:
```bash
git worktree add ../worktree new/branch-name
```

---

### 3. Enter the worktree and publish the branch to remote
```bash
cd ../worktree
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

**Scenario**: You're on your branch, and `main` has new commits you need.

#### Step 1: Update your local copy of `main`
```bash
git fetch origin
```
This downloads the latest `main` from GitHub (doesn't change your current branch).

---

#### Step 2: Choose one approach

**Option A — Rebase (linear history, cleaner):**
```bash
git rebase origin/main
```
- Replays your commits **on top of** the latest `main`
- Result: straight line of commits (no merge commit)
- Use this if you want a clean history
- ⚠️ Rewrites your commit hashes

**Option B — Merge (preserves history):**
```bash
git merge origin/main
```
- Creates a **merge commit** combining both histories
- Result: shows that you merged `main` in
- Use this if you prefer safety and clarity
- Keeps your commits unchanged

---

#### Step 3: If you used rebase, push with `--force-with-lease`
```bash
git push --force-with-lease
```
- Safer than `--force` (won't overwrite others' changes)
- Use this only after rebase (because rebase rewrites history)
- ❌ Don't use with merge (just use `git push`)

---

## 🔀 Create and merge a Pull Request (PR)

```bash
cd /project/directory/path/worktree-1
gh pr create -f -t "Pull Request Title" -b "Adds --explanation about the changes"
```
- `-f` : skips interactive mode, uses current branch
- `-t` : PR title
- `-b` : PR description/body
```bash
gh pr merge --delete-branch
```
- `--delete-branch` : removes the remote branch after merging
- `--squash` (optional) : creates a single commit on `main` (omit to preserve all commits)

---

## 🧹 Update main and cleanup when you're done

From the main repo:
```bash
cd /path/to/main-local-repo
# 1. update main 
git pull origin main

# 2. Remove folder and link
git worktree remove ../worktree
  
# 3. Delete local branch  
git branch -d local/branch

# 4. Delete remote branch (optional)          
git push origin --delete remote/branch         
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