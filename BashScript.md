# 📝 Bash Comments and Documentation Guide

Bash allows developers to add **comments** — lines ignored by the shell — to explain code, mark sections, or temporarily disable commands.  
Comments improve readability, maintainability, and teamwork in software projects.

---

## 🔹 1. Single-Line Comments

```bash
# This is a single-line comment
echo "Hello, world!"  # Inline comment after a command
```

**Explanation:**  
- A single-line comment begins with `#`.  
- The shell ignores everything after `#` on that line.  
- Often used to explain what the next command does or why it’s needed.

---

## 🔹 2. Multi-Line Comments (Using `:` or `<<`)

### Option A — Using a "no-op" (`:`) Command

```bash
: '
This is a multi-line comment.
It uses the colon built-in command (a "no-op").
Everything inside the quotes is ignored.
'
echo "Script continues here."
```

**Explanation:**  
- The colon `:` is a special Bash command that **does nothing** (no operation).  
- Wrapping text in `: ' ... '` effectively skips that block.

---

### Option B — Using a Here Document (`<<`)

```bash
<<COMMENT
This is another way to make
a multi-line comment in Bash.
The shell ignores all lines until COMMENT.
COMMENT
```

**Explanation:**  
- `<<WORD` starts a *here-document*, which sends a block of text to a command.  
- When not attached to a command, it’s effectively ignored by Bash.  
- The block ends when the same `WORD` appears again.

---

## 🔹 3. Commenting Out Code Temporarily

```bash
# git add .
# git commit -m "Testing new script"
git status
```

**Explanation:**  
- Prefixing commands with `#` lets you disable them without deleting.  
- Useful for debugging or testing scripts safely.

---

## 🔹 4. Documentation Blocks (Header Comments)

```bash
#!/bin/bash
# ==========================================
# Script Name: backup.sh
# Author: Your Name
# Date: 2025-11-06
# Description: Automates project backup with timestamp
# ==========================================
```

**Explanation:**  
- A standard convention for documenting Bash scripts.  
- Helps other developers quickly understand script purpose and usage.  

---

## 🔹 5. Special Comment Indicators

| Symbol | Meaning | Example |
|:--------|:---------|:---------|
| `#!` | **Shebang** — tells the OS which interpreter to use | `#!/bin/bash` |
| `#TODO:` | Marks future work to complete | `#TODO: Add error logging` |
| `#FIXME:` | Marks code that needs repair | `#FIXME: Handle missing arguments` |
| `#NOTE:` | Adds extra explanation or warning | `#NOTE: This script overwrites old files` |

---

## ✅ Best Practices

- Use comments to **explain “why”**, not “what” — the code already shows what it does.  
- Keep comments short and consistent.  
- Include a header at the top of every script.  
- Comment out debugging commands instead of deleting them.  

---

## 🧠 Example: Well-Commented Bash Script

```bash
#!/bin/bash
# ==========================================
# Script: auto_backup.sh
# Purpose: Back up a directory with timestamp
# Usage: ./auto_backup.sh /path/to/folder
# ==========================================

# Get current date
DATE=$(date +%Y-%m-%d_%H-%M-%S)

# Check if argument provided
if [ -z "$1" ]; then
  echo "Usage: $0 <source_directory>"
  exit 1
fi

# Create backup directory
mkdir -p ~/Backups

# Copy files
cp -r "$1" ~/Backups/backup_$DATE

#TODO: Add zip compression in future version
echo "✅ Backup complete at ~/Backups/backup_$DATE"
```

---

> 💡 **Tip:**  
> When sharing Bash scripts on GitHub, comments are key to helping others understand your work — especially in collaborative projects.
