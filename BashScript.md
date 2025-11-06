# 🧠 Bash Essentials and Command Reference

Bash (Bourne Again Shell) is a **command-line interpreter** used on Unix-like systems such as Linux and macOS.  
It allows developers to execute commands, automate tasks, and build software efficiently.

---

## ⚙️ Key Applications of Bash

- **Automation**: Run unit tests, build code, and deploy software automatically.  
- **File Management**: Create, move, rename, and delete files or directories.  
- **System Administration**: Manage processes, monitor system status, and schedule tasks.  
- **Development Workflow**: Integrate with Git, Docker, and CI/CD pipelines.  
- **Scripting**: Combine multiple commands into `.sh` scripts for repeatable tasks.

---

## 💻 Common Bash Commands

| Command | Description | Example |
|:---------|:-------------|:---------|
| `pwd` | Print current working directory | `pwd` |
| `ls` | List files and directories | `ls -la` |
| `cd` | Change directory | `cd Documents` |
| `mkdir` | Create a new directory | `mkdir project` |
| `rmdir` | Remove an empty directory | `rmdir old_folder` |
| `touch` | Create a new empty file | `touch script.sh` |
| `cp` | Copy files or directories | `cp file1.txt backup/` |
| `mv` | Move or rename files | `mv file.txt newname.txt` |
| `rm` | Remove files or directories | `rm file.txt` |
| `cat` | Display file contents | `cat notes.txt` |
| `echo` | Print text or variable to terminal | `echo "Hello, world!"` |
| `chmod` | Change file permissions | `chmod +x script.sh` |
| `chown` | Change file ownership | `sudo chown user file.txt` |
| `grep` | Search for text in files | `grep "error" logfile.txt` |
| `find` | Search for files | `find . -name "*.sh"` |
| `man` | Show command manual | `man ls` |
| `history` | Show previous commands | `history` |
| `clear` | Clear terminal screen | `clear` |
| `exit` | Close the terminal or script | `exit` |

---

## 🚀 Running and Executing Bash Scripts

1. **Create a new script file**
   ```bash
   touch hello.sh
   ```

2. **Edit the script**
   ```bash
   cat > hello.sh
   ```
   Paste this inside:
   ```bash
   #!/bin/bash
   echo "Hello, Bash World!"
   ```
   Press **Ctrl + D** to save.

3. **Make it executable**
   ```bash
   chmod +x hello.sh
   ```

4. **Run the script**
   ```bash
   ./hello.sh
   ```

   Output:
   ```bash
   Hello, Bash World!
   ```

---

## 🧰 Example: Automating Code Deployment

```bash
#!/bin/bash
# Simple auto-deploy script

echo "Building project..."
make

if [ $? -eq 0 ]; then
  echo "Build successful, pushing to Git..."
  git add .
  git commit -m "Automated deployment"
  git push
else
  echo "❌ Build failed, check errors."
fi
```

**Explanation:**  
- `make` compiles the project.  
- `$?` checks if the previous command succeeded.  
- `git` commands automate version control actions.  

---

## 🧭 Tips for Using Bash Efficiently

- Use `Tab` for autocompletion of commands and paths.  
- Use `&&` to chain commands (only run next if previous succeeded).  
  Example: `mkdir test && cd test`  
- Use `;` to run multiple commands regardless of success.  
  Example: `cd /tmp; ls; pwd`  
- Use `|` (pipe) to send one command’s output into another.  
  Example: `ls | grep "txt"`  
- Always start scripts with `#!/bin/bash`.  

---

## 📘 Summary

| Topic | Description |
|--------|--------------|
| **Interpreter** | Bash runs commands line by line |
| **Automation** | Great for CI/CD and build scripts |
| **File Management** | Handles directories and data |
| **Scripting** | Saves time on repetitive tasks |

---

> 💡 **Pro Tip:** Keep your Bash scripts modular and well-commented for maintainability.  
> Example: use functions to group related commands and comments to explain logic.
