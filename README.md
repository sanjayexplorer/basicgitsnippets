📁 Basic Git Snippets
Author: Sanjay Explorer 2iQUKWqdx1NeXRVM

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

FOR INSTALL TAILWIND IN LARAVEL PROJECT

1. upload tailwindcss file in root project folder
2. then create tailwind-input.css in public/css/tailwind-input.css
3. then paste these lines in tailwind-input.cs ->>>>>>>>>>>>>>>>> @tailwind base;
@tailwind components;
@tailwind utilities;
then make tailwind.config.js file in project root folder and paste these lines
/** @type {import('tailwindcss').Config} */
module.exports = {
    content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./resources/**/*.vue",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

then run this command ->>>>>>>>>>>>>>>>>>> ./tailwindcss -i public/css/tailwind-input.css -o public/css/tailwind-output.css --watch 
then you can include tailwind-output.css in layout page 

 
