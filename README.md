# code4dummies 📚
[![CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc/4.0/)

Practical cheat sheets and beginner-friendly guides for developers learning **Git**, **GitHub CLI**, and **terminal commands**. Written to explain the "why" behind each command, not just the "what."

---

## 📖 What's Inside?

### 🔗 GitHub & Git (`github4dummies/`)

| Guide | Focus |
|-------|-------|
| [clean_worktree_branch_workflow.md](github4dummies/clean_worktree_branch_workflow.md) | Git worktrees, branching strategy, and safe collaboration patterns |
| [gh_cli_cheet_sheet.md](github4dummies/gh_cli_cheet_sheet.md) | Repository management, issues, PRs, and GitHub CLI authentication |
| [log_inspection_cheat_sheet.md](github4dummies/log_inspection_cheat_sheet.md) | Git log navigation and retrieving deleted files from history |

**Key concept**: Use **Git worktrees** to work on multiple branches simultaneously in separate folders—avoids checkout overhead and dependency conflicts.

### 💻 Terminal (`terminal4dummies/`)

| Guide | Focus |
|-------|-------|
| [terminal-cheat-sheet.md](terminal4dummies/terminal-cheat-sheet.md) | Common macOS/Unix commands with translations and bilingual examples |

---

## 🎯 Core Workflows

### Recommended Git Workflow

1. **Start from updated `main`**
   ```bash
   git checkout main && git pull origin main
   ```

2. **Create branch + worktree in one step**
   ```bash
   git worktree add ../new-folder -b feat/feature-name
   ```

3. **Publish to remote**
   ```bash
   cd ../new-folder
   git push -u origin feat/feature-name
   ```

4. **Make changes and commit**
   ```bash
   git add -A
   git commit -m "Clear commit message"
   git push
   ```

5. **Create and merge PR**
   ```bash
   gh pr create -f -t "PR Title" -b "Description"
   gh pr merge --squash --delete-branch
   ```

6. **Cleanup**
   ```bash
   git worktree remove ../new-folder
   git branch -d feat/feature-name
   ```

**Mental model**:
```
main (stable)
│
└── feat/feature-name  ← (separate worktree)
      ↓ commit / push
      ↓ PR / merge
      ↓ cleanup
```

---

## 💡 Key Principles

✅ **Beginner-friendly** — Explains what each command does and why  
✅ **Real-world examples** — Practical use cases with expected output  
✅ **Safety-first** — Documents safer alternatives (e.g., `--force-with-lease` vs `--force`)  
✅ **Self-contained** — Each guide stands alone with tables and quick references  
✅ **Audience-focused** — No assumptions about prior knowledge  

---

## 🚀 Getting Started

1. **Browse by topic**: Pick a guide based on what you want to learn
2. **Read sequentially**: Each section builds on previous concepts
3. **Reference the tables**: Quick-lookup tables for flags and options
4. **Try the examples**: Each command is tested and works as shown

---

## 📝 How to Use These Guides

- **For learning**: Start from the beginning of each guide
- **For reference**: Use the quick-reference tables and summaries
- **For troubleshooting**: Check the "gotchas" and safety tips sections

**Tip**: Open guides in a split editor pane alongside your terminal for easy reference.

---

## 🤝 Contributing

Found an issue? Want to improve a guide?

1. Create an issue with details about what's unclear or incorrect
2. Open a PR with improvements
3. Reference the relevant section in your commit message

**Content guidelines**:
- Target beginners—explain concepts before commands
- Include expected output for commands
- Use tables for comparing options
- Document the "why" behind recommendations

---

## 📦 Project Structure

```
code4dummies/
├── README.md                          # This file
├── .github/
│   └── copilot-instructions.md       # AI agent guidelines
├── github4dummies/
│   ├── clean_worktree_branch_workflow.md
│   ├── gh_cli_cheet_sheet.md
│   └── log_inspection_cheat_sheet.md
└── terminal4dummies/
    └── terminal-cheat-sheet.md
```

---

## 🎓 Learning Path (Recommended Order)

1. **New to Git?** Start with [clean_worktree_branch_workflow.md](github4dummies/clean_worktree_branch_workflow.md)
2. **Need GitHub CLI?** Read [gh_cli_cheet_sheet.md](github4dummies/gh_cli_cheet_sheet.md)
3. **Lost a file?** Check [log_inspection_cheat_sheet.md](github4dummies/log_inspection_cheat_sheet.md)
4. **Terminal basics?** See [terminal-cheat-sheet.md](terminal4dummies/terminal-cheat-sheet.md)

---

## ⚖️ License

CC-BY-NC-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 

---

## 📬 Questions?

These guides are living documents. If something is unclear or needs updating, please open an issue or submit a PR.

**Happy learning! 🚀**
