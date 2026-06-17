# Linux Fundamentals Part 1
### TryHackMe — Cyber Security 101 Path

---

## What this room was about

Introduction to navigating a Linux system through 
the command line. Covered essential commands for 
file system navigation, reading file contents, 
searching for files and text, and using Linux 
operators to control command behaviour.

All practical tasks completed inside TryHackMe's 
browser-based Linux virtual machine.

---

## Commands I learned and used

### Navigation & File System

| Command | Full name | What it does |
|---|---|---|
| `ls` | List | Lists files and folders in current directory |
| `cd` | Change Directory | Move into a different folder |
| `pwd` | Print Working Directory | Shows your exact location in the file system |
| `cat` | Concatenate | Displays the contents of a file |
| `echo` | Echo | Outputs any text you provide to the terminal |
| `whoami` | Who Am I | Shows which user you are currently logged in as |

### Searching & Finding

| Command | What it does |
|---|---|
| `find -name passwords.txt` | Searches for a specific file by name |
| `find -name *.txt` | Finds all files with .txt extension using wildcard |
| `grep 'keyword' filename` | Searches inside a file for specific text |
| `grep -R 'keyword' /directory/` | Searches recursively through all files in a directory |

### Linux Operators

| Operator | What it does |
|---|---|
| `&` | Runs a command in the background |
| `&&` | Runs two commands in sequence — second only runs if first succeeds |
| `>` | Redirects output to a file — overwrites existing content |
| `>>` | Redirects output to a file — appends without overwriting |

---

## Key things I actually learned

- `ls` shows nothing if a directory is empty — 
  this is normal
- `cat` can read files without navigating to them 
  first: `cat /home/ubuntu/Documents/todo.txt`
- `find` with a wildcard `*` searches for file 
  types across the whole directory
- `grep -R` is powerful for searching multiple 
  files at once — useful when looking for 
  passwords or config values hidden in files
- The difference between `>` and `>>` matters — 
  using `>` will wipe existing file contents, 
  `>>` safely adds to the end
- `&&` only runs the second command if the first 
  succeeded — useful for chaining commands safely

---

## Practical exercises completed

- Listed files in directories using ls
- Navigated between directories using cd and pwd
- Read file contents using cat
- Used find to locate hidden files by name 
  and extension
- Used grep to search file contents for 
  specific values
- Practiced output redirection using > and >>
- Used echo to write text into files

---

## Why this matters for SOC work

These commands are used constantly during Linux 
incident response investigations:

- `find -name *.sh` — locate suspicious scripts 
  dropped by attackers
- `grep -R 'password' /var/www/` — search for 
  exposed credentials in web directories  
- `cat /var/log/auth.log` — read authentication 
  logs to investigate unauthorised access
- `pwd` and `ls -la` — orient yourself quickly 
  on an unfamiliar compromised system
- `>>` — append investigation notes to a file 
  without losing previous findings

Understanding these fundamentals means when you 
land on a compromised Linux machine during an 
investigation you can navigate, search, and 
read evidence immediately without hesitation.

---

*Source: TryHackMe Cyber Security 101 — 
Linux Fundamentals Part 1*
*Completed as part of ongoing SOC analyst preparation*
