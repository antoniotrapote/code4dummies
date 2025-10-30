## 2. Manage Issues with GitHub CLI

### 2.1. Create a new issue
```bash
gh issue create --title "Update README.md" --body "- [x] Updated title\n- [ ] Added project summary\n- [ ] Updated structure" --label documentation
```

**Options:**
- `--title` → issue title  
- `--body` → description (Markdown supported)  
- `--label` → assign one or more labels  

---

### 2.2. List issues
```bash
gh issue list
```
Show all open issues for the current repository.

Additional filters:
```bash
gh issue list --state all
gh issue list --label documentation
```

---

### 2.3. View an issue
```bash
gh issue view 1
```
View details, description, and comments for issue #1.

Open directly in the browser:
```bash
gh issue view 1 --web
```

---

### 2.4. Edit an issue
```bash
gh issue edit 1 --add-label enhancement
gh issue edit 1 --body "Added project summary and structure updates."
```

---

### 2.5. Close an issue
```bash
gh issue close 1 --comment "README updated successfully!"
```
Or close it via the GitHub web interface:
```bash
gh issue close 1 --web
```

---

### 6. Reopen a closed issue
```bash
gh issue reopen 1
```

---

### Quick reference table

| Action           | Command example                                   | Description |
|------------------|---------------------------------------------------|-------------|
| Create issue     | `gh issue create --title "..." --body "..."`      | Create a new task |
| List issues      | `gh issue list`                                   | Show open issues |
| View issue       | `gh issue view <num>`                             | Read details & comments |
| Edit issue       | `gh issue edit <num> --add-label ...`             | Modify labels or description |
| Close issue      | `gh issue close <num>`                            | Mark issue as completed |
| Reopen issue     | `gh issue reopen <num>`                           | Reopen a closed issue |

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 