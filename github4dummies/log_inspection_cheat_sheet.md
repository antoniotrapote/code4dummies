# Viewing Git Logs from Terminal

When you run `git log`, Git opens a **pager** (usually `less`) to let you scroll through your commits.  
While in this mode, the terminal behaves like a text viewer — not like a command prompt.

---

## ⌨️ Navigation keys inside `git log`
| Key | Action |
|-----|--------|
| ↑ / ↓ | Move up or down one line |
| Space | Move forward one page |
| b | Move backward one page |
| g | Go to the beginning |
| G | Go to the end |
| /text | Search for text |
| n | Next search result |
| q | **Quit (exit viewer)** |

---

## 💡 Tips to view logs without the pager

If you prefer the output to appear directly in the terminal (no viewer mode):

```bash
git --no-pager log
```

Show only the last 3 commits:
```bash
git log -3
```

Compact view (one line per commit):
```bash
git log --oneline
```

Example output:
```
d6474b5 Initial commit
4ab9f3e Add README
c91de77 Update dependencies
```

---

## 🔍 Read deleted files from Git history
You can view the contents of a deleted file directly from the log using its commit hash.

```bash
# Show all commits
git log   

# Find the last commit that contained a specific file                       
git log -- path/to/file.ext    

# View the file content from that commit
git show <commit_hash>:path/to/file.ext
```

---
CC-BY-4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 
