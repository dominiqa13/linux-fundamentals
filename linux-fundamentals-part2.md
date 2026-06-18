# Linux Fundamentals Part 2
### TryHackMe — Cyber Security 101 Path

---

## What this room was about

Building on Linux basics — learned file and folder 
management, flags and switches, file permissions, 
user switching, and key Linux directory structure. 
All practical tasks completed inside TryHackMe's 
browser-based Linux virtual machine.

---

## Commands I learned and used

### File & Folder Management

| Command | Full Name | What it does |
|---|---|---|
| `touch filename` | Touch | Creates a new empty file |
| `mkdir foldername` | Make Directory | Creates a new folder |
| `cp file1 file2` | Copy | Copies a file and gives it a new name |
| `mv file1 file2` | Move | Moves or renames a file |
| `rm filename` | Remove | Deletes a file |
| `rm -R foldername` | Remove Recursive | Deletes a folder and everything inside it |
| `file filename` | File | Identifies what type of file something is |

### Flags & Switches

| Command | What it does |
|---|---|
| `ls -a` | Lists all files including hidden ones starting with . |
| `ls -l` | Lists files with detailed info — permissions, owner, size |
| `ls -la` | Combines both — detailed view including hidden files |
| `man ls` | Opens the manual page for any command |

### User Management

| Command | What it does |
|---|---|
| `su username` | Switch to another user account |
| `su -l username` | Switch user and inherit their full environment |

### SSH

| Command | What it does |
|---|---|
| `ssh username@10.10.x.x` | Connect to a remote machine securely |

---

## File Permissions — How They Work

Every file on Linux has three permission groups:

| Group | Who it applies to |
|---|---|
| First 3 characters | The owner of the file |
| Next 3 characters | The group assigned to the file |
| Last 3 characters | Everyone else |

Each group can have three permissions:

| Letter | Permission | Numeric value |
|---|---|---|
| r | Read | 4 |
| w | Write | 2 |
| x | Execute | 1 |

To calculate the numeric permission — add the values:

| Symbolic | Calculation | Numeric | Meaning |
|---|---|---|---|
| rwx | 4+2+1 | 7 | Full access |
| r-x | 4+0+1 | 5 | Read and execute only |
| r-- | 4+0+0 | 4 | Read only |
| --- | 0+0+0 | 0 | No access at all |

**Common permission examples:**

| Symbolic | Numeric | Meaning |
|---|---|---|
| rwxrwxrwx | 777 | Everyone has full access |
| rwxr-xr-x | 755 | Owner full, others read and execute |
| rw-r--r-- | 644 | Owner read/write, others read only |
| rwx------ | 700 | Only owner has any access |

**How to change permissions:**
```bash
chmod 755 filename
chmod 644 filename
```

---

## Key Linux Directories — Essential for SOC Work

| Directory | What it contains | SOC relevance |
|---|---|---|
| `/etc` | System configuration files | Contains passwd, shadow, and sudoers files — check for unauthorised changes |
| `/etc/passwd` | List of all user accounts | Check for accounts created by attackers |
| `/etc/shadow` | Encrypted password hashes | Target for attackers attempting credential theft |
| `/etc/sudoers` | Users allowed to run sudo | Attackers modify this to gain persistent root access |
| `/var` | Variable data — frequently changing | Contains logs and databases |
| `/var/log` | System and application logs | First place to check during any investigation |
| `/root` | Home directory for root user | Attacker's target — gaining access here means full control |
| `/tmp` | Temporary files — cleared on reboot | Attackers commonly drop malicious scripts here — always check |

---

## Key things I actually learned

- Hidden files on Linux start with a dot — 
  use `ls -a` to see them
- `mv` can both move AND rename files — 
  same command, two uses
- `rm -R` deletes everything inside a folder 
  recursively — be careful with this
- The `file` command identifies what a file 
  actually is regardless of its extension — 
  attackers often rename malware to hide it
- `man` before any command shows its full 
  documentation — useful when you forget flags
- `/tmp` is world-writable — any user can 
  write there — a common attacker staging area
- `su -l` gives you a full login shell as 
  another user, not just a basic switch

---

## Why this matters for SOC work

**File permissions** — misconfigured permissions 
are a common vulnerability. A file with 777 
permissions means anyone can modify it — 
including attackers. Spotting world-writable 
sensitive files is a key investigation skill.

**The /tmp directory** — one of the first places 
to check on a compromised Linux system. Attackers 
drop scripts, tools, and malware here because 
any user can write to it without special permissions.

**The /etc/passwd and /etc/shadow files** — 
checking these for new or unusual accounts is 
standard practice after a suspected compromise. 
A new account you don't recognise = potential 
attacker persistence.

**The /var/log directory** — this is where all 
the evidence lives. auth.log, syslog, and 
application logs all sit here. Knowing this 
directory exists and how to navigate to it 
quickly is essential for incident response.

---

## Practical exercises completed

- Created and deleted files and folders using 
  touch, mkdir, rm
- Copied and renamed files using cp and mv
- Used ls -la to reveal hidden files
- Read manual pages using man
- Switched between user accounts using su
- Analysed file permissions in symbolic and 
  numeric format
- Explored key Linux system directories

---

*Source: TryHackMe Cyber Security 101 — 
Linux Fundamentals Part 2*  
*Completed as part of ongoing SOC analyst preparation*
