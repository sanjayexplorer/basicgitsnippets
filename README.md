# Basic Git Snippets

**Author:** Sanjay Explorer 2iQUKWqdx1NeXRVM

A quick, practical reference for common Git commands and workflows.

## Git Configuration

### Set global Git user
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Check global Git config
```bash
git config --global user.name
git config --global user.email
```

### Set local Git user (for a specific repository)
```bash
git config user.name "Your Name"
git config user.email "your.email@example.com"
```

### List all config settings
```bash
git config --list
```

## Remote Repository

### Add a remote origin
```bash
git remote add origin <repository_url>
# Example:
git remote add origin https://github.com/sanjayexplorer/basicgitsnippets
```

### View remote URLs
```bash
git remote -v
```

### Change remote URL
```bash
git remote set-url origin <new_url>
```

### Clone a repository
```bash
git clone <repository_url>
# Example:
git clone https://github.com/sanjayexplorer/basicgitsnippets
```

## Git Basics

### Check the hidden .git folder
```bash
ls -a
```

### Check status
```bash
git status
```

## Git File Status Lifecycle

**untracked → modified → staged → committed → unmodified**

- **Untracked:** New files not tracked by Git.
- **Modified:** Tracked files with changes.
- **Staged:** Files added and ready to commit.
- **Committed:** Changes saved to the local repo.
- **Unmodified:** Files with no changes.

## Example Workflow

```bash
# 1. Check changes
git status

# 2. Stage files
git add .

# 3. Commit changes
git commit -m "Your message"

# 4. Push to GitHub
git push origin main
```

## Working with Branches

### Create a branch
```bash
git branch <branch_name>
```

### Switch to a branch
```bash
git checkout <branch_name>
```

### Create and switch to a new branch
```bash
git checkout -b <branch_name>
```

### Merge a branch into main
```bash
git checkout main
git merge <branch_name>
```

## Undo Changes

### Unstage a file
```bash
git reset <file>
```

### Discard local changes
```bash
git checkout -- <file>
```

### Undo last commit (keep changes)
```bash
git reset --soft HEAD~1
```

### Undo last commit (discard changes)
```bash
git reset --hard HEAD~1
```

## Clean & Reset

### Remove untracked files
```bash
git clean -f
```

### Remove untracked files and directories
```bash
git clean -fd
```

### Reset to the last commit
```bash
git reset --hard
```

## Viewing History

### View commit history
```bash
git log
```

### One-line history
```bash
git log --oneline
```

### View file history
```bash
git log <file>
```

## Install Tailwind CSS in a Laravel Project

1. **Download** the Tailwind CSS binary and place it in the project root.
2. **Create** `public/css/tailwind-input.css` and add:
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```
3. **Create** `tailwind.config.js` in the project root with:
   ```js
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
   };
   ```
4. **Build Tailwind CSS**:
   ```bash
   ./tailwindcss -i public/css/tailwind-input.css -o public/css/tailwind-output.css --watch
   ```
5. **Include** `tailwind-output.css` in your layout page.
