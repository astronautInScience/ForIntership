# 🖥️ Bash: Command-Line Power and Automation

## 🔹 Overview
**Bash** (short for *Bourne Again Shell*) is a **command-line interpreter** that allows users to interact with their operating system by typing commands.  
It is available on most Unix-like systems, including **Linux** and **macOS**.  

Developers and system administrators use Bash to **automate repetitive tasks**, manage files, and run complex system operations efficiently.

---

## ⚙️ Key Features of Bash
- Execute system commands directly from the terminal  
- Use **variables**, **loops**, and **conditional statements** to create powerful scripts  
- Automate workflows using small, readable scripts  
- Combine multiple Linux tools (like `grep`, `sed`, `awk`) for data processing  
- Manage files, permissions, and system updates automatically  

---

## 💻 Bash in Software Development
Bash is widely used in professional software development for:

1. **Automation**
   - Automating unit tests and deployment steps  
   - Running CI/CD pipelines  
   - Managing repetitive project setup tasks  

2. **Build Systems**
   - Compiling code and preparing build artifacts  

3. **Version Control Integration**
   - Interacting with Git repositories  
   - Simplifying commit and push operations  

4. **Server Management**
   - Deploying applications remotely  
   - Monitoring and maintaining servers  

---

## 🚀 Example Project — *Git Auto Commit and Push Script*

This script automates the process of adding, committing, and pushing code to a Git repository — something every developer does daily.

```bash
#!/bin/bash
# === Git Auto Commit and Push Script ===

# Colors for messages
GREEN="\033[0;32m"
RED="\033[0;31m"
YELLOW="\033[1;33m"
NC="\033[0m" # No color

# Check if the directory is a Git repo
if [ ! -d ".git" ]; then
  echo -e "${RED}Error:${NC} Not a Git repository."
  exit 1
fi

# Display Git status
echo -e "${YELLOW}Checking Git status...${NC}"
git status

# Ask for commit message
echo -e "${YELLOW}Enter commit message:${NC}"
read message

# Add, commit, and push changes
git add .
git commit -m "$message"

if [ $? -ne 0 ]; then
  echo -e "${RED}Commit failed!${NC}"
  exit 1
fi

echo -e "${GREEN}Pushing to remote...${NC}"
git push

if [ $? -eq 0 ]; then
  echo -e "${GREEN}✅ Push successful!${NC}"
else
  echo -e "${RED}❌ Push failed.${NC}"
fi

chmod +x gitpush.sh
./gitpush.sh
