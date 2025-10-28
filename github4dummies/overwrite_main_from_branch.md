# Overwrite Main from Branch

Step-by-step guide to **replace `main`** with work from another branch using **Pull Request** (preferred) or **forced overwrite**. Includes **which folder** to execute each command from when working with **worktrees**.

## 📁 Context
- `/project/directory/path/project-name-main` → **main**
- `/project/directory/path/worktree-1` → **exp/feature**
- `/project/directory/path/worktree-2` → **exp/feature2**

---

## ✅ Method A — PR / Merge (Preferred, No Force)
Use this method if `main` doesn't have its own commits that you want to keep divergent from `exp/feature` (ideal: fast-forward).

### 1) Publish and ensure `exp/feature` is ready
**From** `/project/directory/path/worktree-1`:
```bash
cd /project/directory/path/worktree-1
git status                       # On branch exp/feature
git add -A
git commit -m "final commit before PR" || true
git push -u origin exp/feature
```

### 2) Create a Pull Request to `main`
**From** the same folder (`/worktree-1`):
```bash
gh pr create -B main -H exp/feature -t "Overwrite main with exp/feature" -b "Promote feature work to main"
```
- `-B main`: base branch (PR destination)
- `-H exp/feature`: head branch (your work)
- `-t`: PR title
- `-b`: PR description

### 3) Merge the PR
**From** the same folder (`/worktree-1`):
```bash
gh pr merge --squash --delete-branch
```
> `--squash` creates a single commit on `main`. You can omit it to preserve all commits.

### 4) Update `main` and cleanup
**From** `/project/directory/path/project-name-main`:
```bash
cd /project/directory/path/project-name-main
git pull origin main
```

**Delete the worktree, local branch, and remote branch** (if it still exists):
```bash
git worktree remove /project/directory/path/worktree-1
git branch -d exp/feature
git push origin --delete exp/feature
```

**Sync and prune deleted remote branches:**
```bash
git fetch --prune                # sync and remove deleted branches
git remote prune origin          # clean up stale remote references
```

---

## Method B — Complete Overwrite (Forced)
Use this method if you want `main` to be **identical** to `exp/feature` even if `main` has changed independently.

### 1) Publish and ensure `exp/feature` is ready
**From** `/project/directory/path/worktree-1`:
```bash
cd /project/directory/path/worktree-1
git status
git add -A
git commit -m "final before overwrite main" || true
git push -u origin exp/feature
```

### 2) Replace local `main` with `exp/feature`
**From** `/project/directory/path/project-name-main` (main worktree):
```bash
cd /project/directory/path/project-name-main
git status                  # On branch main
git pull origin main        # update local reference

# Try fast-forward (clean). If it works, you're done.
git merge --ff-only exp/feature

# If fast-forward is not possible, overwrite completely:
git reset --hard exp/feature
```

### 3) Publish the new `main` (forced if you did reset)
**From** `/project/directory/path/project-name-main`:
```bash
git push origin main --force
```
> ⚠️ If `main` is protected, you'll need to use the PR method or temporarily adjust protection rules.

### 4) Final cleanup (worktree + branches)
```bash
git worktree remove /project/directory/path/worktree-1
git branch -d exp/feature
git push origin --delete exp/feature
```

---

## 🔍 Useful Checks
```bash
git worktree list
# Expected at the end:
# /.../project-name-main   <hash> [main]
# /.../worktree-1          <hash> [exp/feature]

git log --oneline --decorate --graph -n 5
# Verify that main points to the expected commit
```

---

## 🧠 Anti-Error Tips
- **Never switch branches within a worktree.** Each worktree is tied to a single fixed branch.
- Run commands **in the correct worktree folder** (indicated above in each step).
- Before dangerous operations (`reset --hard`, `push --force`), make sure you've **pushed your work branch** to remote (step 1 of each method).
- For teams, **prefer the PR method**. Forced overwrite is for controlled, solo scenarios.
- Always verify your branch is up-to-date before merging: `git pull origin branch-name`

---

CC-BY-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 
