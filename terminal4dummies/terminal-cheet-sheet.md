
# macOS/Unix terminal cheat sheet

## 📂 COMMON COMMANDS (Unix/macOS)
---

Command | Full Word                  | Meaning
--------|----------------------------|-------------------------------
cd      | change directory           | Change directory
ls      | list                       | List files/folders
pwd     | print working directory    | Print current directory path
mkdir   | make directory             | Create directory
rmdir   | remove directory           | Remove empty directory
rm      | remove                     | Delete file(s)
cp      | copy                       | Copy
mv      | move                       | Move or rename
touch   | (full word)                | Create empty file / update timestamp
cat     | concatenate                | Display file contents
less    | (full word)                | View content paginated
head    | (full word)                | Show first lines
tail    | (full word)                | Show last lines
echo    | (full word)                | Print text
man     | manual                     | Show command manual
whoami  | (full word)                | Show current user
history | (full word)                | Show command history
open    | (full word, macOS)         | Open file with default app
kill    | (full word)                | Terminate a process

---

## 📖 BASIC EXAMPLES
---

# Navigation
```bash
pwd                # show where I am
cd ~/Projects      # navigate to Projects folder in home directory
cd ..              # go up one level
ls -la             # list files, including hidden files and details 
                   # -l : long format, -a : all files 
```

# Create, copy, move, delete
```bash
mkdir test                  # create a folder named "test"
touch hello.txt             # create an empty file
echo "Hello!" > hello.txt   # create a file with text
cp hello.txt copy.txt       # copy file
mv copy.txt renamed.txt     # rename/move file
rm renamed.txt              # delete file
rm -rf test                 # delete folder and all contents (careful!)
                            # -r : recursive, -f : force
```

# View contents
```bash
open "file"          # open file  
cat hello.txt        # show complete content
less hello.txt       # show paginated (q to exit)
head hello.txt       # first 10 lines
tail hello.txt       # last 10 lines
```

# Edit files
```bash
nano hello.txt       # edit file with nano text editor
vim hello.txt        # edit file with vim text editor
```

# Search
```bash
grep "Hello" hello.txt  # search for word in file
find . -name "*.txt"    # find all .txt files from current directory
```

# Other useful commands
```bash
diskutil eject /Volumes/diskname  # safely eject a disk
unzip file.zip                    # unzip file
unzip file.zip -d ~/Destination 
history                           # recent commands
clear                             # clear screen (Ctrl+L)
man ls                            # manual for the ls command
```

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 