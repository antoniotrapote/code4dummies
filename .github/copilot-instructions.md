# AI Coding Agent Instructions for code4dummies

## Project Overview
This is an **educational reference repository** containing practical cheat sheets and guides for developers learning Git, GitHub CLI, and terminal commands. It's organized into two main subject domains:

- `github4dummies/`: Git workflows, GitHub CLI, and Git log inspection  
- `terminal4dummies/`: macOS/Unix terminal fundamentals  

**Purpose**: Provide clear, beginner-friendly documentation with real-world examples and step-by-step workflows.

---

## Architecture & File Organization

### Key Files by Domain

**GitHub/Git Domain** (`github4dummies/`):
- `clean_worktree_branch_workflow.md` - Comprehensive guide to Git worktrees, branching strategy, and safe collaboration patterns
- `gh_cli_cheet_sheet.md` - Repository management, issues, PRs, and authentication via GitHub CLI
- `log_inspection_cheat_sheet.md` - Git log navigation and retrieving deleted files from history

**Terminal Domain** (`terminal4dummies/`):
- `terminal-cheat-sheet.md` - Common macOS/Unix commands with translations and examples

Each markdown file is **self-contained** with tables, code blocks, and organized sections.

---

## Content Conventions

### 1. **Audience-First Structure**
Documents target **beginners**, so always include:
- Plain-English explanations before commands
- A quick summary table or checklist at the end
- Real-world use cases ("why you'd do this")

### 2. **Command Examples**
- Use **bash** for `terminal4dummies/` (zsh-compatible)
- Use **bash** for `github4dummies/` (no shell-specific syntax)
- Always explain flags (`--flag` descriptions in tables)
- Show expected output when relevant (e.g., git log output examples)

### 3. **Section Organization Pattern**
```
# Main Topic
## Subtopic  
### Step-by-step guide / Quick reference
- Tables for options/flags
- Code blocks for commands
- 💡 Tips or ⚠️ Warnings
```

**Footer for every new .md file** (at the end):
```markdown
---

CC-BY-4.0 © 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 
```

### 4. **Git/GitHub Workflow Specifics**
- **Worktree philosophy** (from `clean_worktree_branch_workflow.md`): Use Git worktrees to work on multiple branches simultaneously in separate folders—avoids checkout overhead and dependency conflicts
- **Squash-merge PRs**: The recommended merge strategy is `--squash --delete-branch` to keep history clean
- **Upstream configuration**: Always set `-u origin branch-name` when first pushing a new branch
- **Safety-first approach**: Document safer alternatives (e.g., `--force-with-lease` instead of `--force`)

### 5. **Terminal Command Conventions**
- macOS/zsh is the target environment
- Include both full command names and abbreviations (e.g., `cd` = "change directory")
- When modifying files, prefer `echo` or piping over direct editing
- Distinguish between destructive (`rm -rf`) and safe operations

---

## Common Patterns to Preserve

### Git Workflow Pattern
1. Start from updated `main` (`git checkout main && git pull origin main`)
2. Create branch + worktree in one step (`git worktree add ../folder -b branch-name`)
3. Publish to remote immediately (`git push -u origin branch-name`)
4. Make changes, commit, push regularly
5. Create PR via GitHub CLI (`gh pr create`)
6. Merge and cleanup (`git worktree remove` + `git branch -d`)

### Documentation Pattern
- Use **emoji** sparingly but consistently (🧩 concepts, 🪜 steps, ✅ checks, 💾 safe operations)
- Include quick-reference **tables** for related commands
- Provide **mental model** diagrams using ASCII (branch trees, folder structures)

---

## When Adding/Updating Content

**DO:**
- Reference real files from the repo (e.g., "see `clean_worktree_branch_workflow.md` for full steps")
- Include practical gotchas (e.g., "detached HEAD" scenario in branch workflow)
- Use tables for command comparisons and option explanations
- Add examples with realistic output

**DON'T:**
- Assume users know Git internals—explain what each command does
- Omit the "why" behind recommendations (e.g., why `--force-with-lease` over `--force`)
- Mix shell-specific syntax without noting the environment
- Create aspirational content—document only what's actively used in this repo

---

## Author & License
Maintained by: **Antonio L. Martínez Trapote**  
License: **CC-BY-4.0** © 2025
