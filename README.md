📁 Basic Git Snippets
Author: Sanjay Explorer

🔧 Git Configuration
Set Global Git User
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

Check Global Git Config
git config --global user.name
git config --global user.email

🌐 Remote Repository
Add Remote Origin
git remote add origin <repository_url>
# Example:
git remote add origin https://github.com/sanjayexplorer/basicgitsnippets

Clone Repository
git clone <repository_url>
# Example:
git clone https://github.com/sanjayexplorer/basicgitsnippets

📂 Git Basics
Check Hidden .git Folder
ls -a
git status

🔄 Git File Status Lifecycle
untracked -> modified -> staged -> committed -> unmodified
Untracked: New files not tracked by Git

Modified: Tracked files with changes

Staged: Files added and ready to commit

Unmodified: Files with no changes

Example Workflow

# 1. Create or edit files
# 2. Check changes
git status

# 3. Stage files
git add .

# 4. Commit changes
git commit -m "Your message"

# 5. Push to GitHub
git push origin main

