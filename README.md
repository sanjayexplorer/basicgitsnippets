📁 Basic Git Snippets
Author: Sanjay Explorer

🔧 Git Configuration

Set Global Git User
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

Check Global Git Config
git config --global user.name
git config --global user.email

Set Local Git User (for a specific repo)
git config user.name "Your Name"
git config user.email "your.email@example.com"

List All Config Settings
git config --list


🌐 Remote Repository

Add Remote Origin
git remote add origin <repository_url>
# Example:
git remote add origin https://github.com/sanjayexplorer/basicgitsnippets

View Remote URLs
git remote -v

Change Remote URL
git remote set-url origin <new_url>

Clone Repository
git clone <repository_url>
# Example:
git clone https://github.com/sanjayexplorer/basicgitsnippets

📂 Git Basics
Check Hidden .git Folder
ls -a

Check Status
git status

🔄 Git File Status Lifecycle
untracked → modified → staged → committed → unmodified

Untracked: New files not tracked by Git
Modified: Tracked files with changes
Staged: Files added and ready to commit
Committed: Saved to local repo
Unmodified: Files with no changes

🧪 Example Workflow

# 1. Check changes
git status

# 2. Stage files
git add .

# 3. Commit changes
git commit -m "Your message"

# 4. Push to GitHub
git push origin main

📦 Working with Branches
Create a Branch
git branch <branch_name>

Switch to Branch
git checkout <branch_name>

Create and Switch
git checkout -b <branch_name>

Merge Branch into Main
git checkout main
git merge <branch_name>

🔙 Undo Changes

Unstage a File
git reset <file>

Discard Local Changes
git checkout -- <file>

Undo Last Commit (keep changes)
git reset --soft HEAD~1

Undo Last Commit (discard changes)
git reset --hard HEAD~1

🧹 Clean & Reset
Remove Untracked Files
git clean -f

Remove Untracked Files and Dirs
git clean -fd

Reset to Last Commit
git reset --hard

🔍 Viewing History
View Commit History
git log

One-Line History
git log --oneline

View File History
git log <file>

