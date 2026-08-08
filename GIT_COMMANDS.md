# Git Commands Cheat Sheet

A quick reference for commonly used Git and GitHub commands.

---

## 1. Git Basics

### Check Git version

```bash
git --version
```

### Check Git configuration

```bash
git config --list
```

### Set username

```bash
git config --global user.name "Your Name"
```

### Set email

```bash
git config --global user.email "your@email.com"
```

### Check a specific configuration

```bash
git config user.name
git config user.email
```

---

# 2. Creating a Repository

## Initialize a Git repository

Run this inside your project folder:

```bash
git init
```

Creates a `.git` folder and turns the current folder into a Git repository.

### Check repository status

```bash
git status
```

Shows:

* Modified files
* New files
* Staged files
* Current branch

---

# 3. Clone an Existing Repository

Clone a GitHub repository to your computer:

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/username/project.git
```

Then enter the project:

```bash
cd project
```

---

# 4. Checking Files

### List files

Git Bash:

```bash
ls
```

PowerShell:

```powershell
ls
```

### Show hidden files

Git Bash:

```bash
ls -a
```

PowerShell:

```powershell
ls -Force
```

---

# 5. Adding Files

## Add one file

```bash
git add filename
```

Example:

```bash
git add index.html
```

## Add multiple files

```bash
git add file1.js file2.js
```

## Add everything

```bash
git add .
```

This stages all new and modified files in the current directory.

---

# 6. Committing Changes

## Create a commit

```bash
git commit -m "Your commit message"
```

Example:

```bash
git commit -m "Add login page"
```

### View commits

```bash
git log
```

### Compact commit history

```bash
git log --oneline
```

### View recent commits

```bash
git log -5
```

---

# 7. The Basic Git Workflow

The most commonly used sequence:

```bash
git status
git add .
git commit -m "Describe what changed"
git push
```

Typical workflow:

```text
Modify files
     ↓
git status
     ↓
git add .
     ↓
git commit
     ↓
git push
```

---

# 8. Branches

## Show current branch

```bash
git branch
```

## Create a branch

```bash
git branch branch-name
```

Example:

```bash
git branch feature-login
```

## Create and switch to a branch

```bash
git checkout -b feature-login
```

Modern alternative:

```bash
git switch -c feature-login
```

## Switch branches

```bash
git switch branch-name
```

Example:

```bash
git switch main
```

Older command:

```bash
git checkout main
```

## Delete a branch

```bash
git branch -d branch-name
```

Force delete:

```bash
git branch -D branch-name
```

---

# 9. Merging Branches

First switch to the branch you want to merge into:

```bash
git switch main
```

Then:

```bash
git merge branch-name
```

Example:

```bash
git switch main
git merge feature-login
```

---

# 10. GitHub Remote Repository

## Add GitHub repository

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/username/project.git
```

## Check remote

```bash
git remote -v
```

## Change remote URL

```bash
git remote set-url origin <new-url>
```

## Remove remote

```bash
git remote remove origin
```

---

# 11. Push to GitHub

## First push

```bash
git push -u origin main
```

The `-u` connects your local `main` branch with the remote `main` branch.

After that, you can usually use:

```bash
git push
```

## Push another branch

```bash
git push -u origin branch-name
```

Example:

```bash
git push -u origin feature-login
```

---

# 12. Pull Changes from GitHub

## Pull latest changes

```bash
git pull
```

Equivalent idea:

```text
git fetch
+
git merge
```

## Pull a specific branch

```bash
git pull origin main
```

---

# 13. Fetch

Download information about remote changes without changing your working files:

```bash
git fetch
```

Fetch from a specific remote:

```bash
git fetch origin
```

---

# 14. Difference Between Git Commands

### git fetch

Downloads changes from GitHub but doesn't merge them.

```bash
git fetch
```

### git pull

Downloads changes and integrates them into your current branch.

```bash
git pull
```

### git push

Uploads your local commits to GitHub.

```bash
git push
```

---

# 15. Checking Changes

## See modified files

```bash
git status
```

## See changes that haven't been staged

```bash
git diff
```

## See staged changes

```bash
git diff --staged
```

---

# 16. Undoing Changes

## Undo changes in a file

```bash
git restore filename
```

Example:

```bash
git restore index.html
```

This removes uncommitted changes from that file.

### Unstage a file

```bash
git restore --staged filename
```

The file remains changed but is removed from the staging area.

---

# 17. Undoing the Last Commit

## Undo commit but keep changes

```bash
git reset --soft HEAD~1
```

The changes remain staged.

## Undo commit and unstage changes

```bash
git reset HEAD~1
```

## Undo commit and delete changes

```bash
git reset --hard HEAD~1
```

⚠️ Be careful with `--hard`. It can permanently remove uncommitted work.

---

# 18. Git Stash

Temporarily save unfinished changes.

## Save changes

```bash
git stash
```

## Show stashes

```bash
git stash list
```

## Restore latest stash

```bash
git stash pop
```

## Apply stash without removing it

```bash
git stash apply
```

## Delete a stash

```bash
git stash drop
```

---

# 19. .gitignore

Create a file named:

```text
.gitignore
```

Use it to tell Git which files/folders should NOT be tracked.

Example:

```gitignore
node_modules/
.env
dist/
*.log
```

Common things to ignore:

```text
node_modules/
.env
dist/
build/
*.log
```

⚠️ Never commit passwords, API keys, secret tokens, or private credentials.

---

# 20. Viewing Remote Information

### Show remote repositories

```bash
git remote -v
```

### Show detailed remote information

```bash
git remote show origin
```

---

# 21. Git Tags

Tags are commonly used to mark versions/releases.

## Create a tag

```bash
git tag v1.0.0
```

## List tags

```bash
git tag
```

## Push a tag

```bash
git push origin v1.0.0
```

## Push all tags

```bash
git push --tags
```

---

# 22. Git Log

### Full history

```bash
git log
```

### One-line history

```bash
git log --oneline
```

### Graph view

```bash
git log --oneline --graph --all
```

### Show a particular commit

```bash
git show <commit-id>
```

Example:

```bash
git show a1b2c3d
```

---

# 23. Comparing Branches

Compare two branches:

```bash
git diff main feature-login
```

Compare commits:

```bash
git diff commit1 commit2
```

---

# 24. Delete Files

Remove a file and stage the deletion:

```bash
git rm filename
```

Example:

```bash
git rm old-file.txt
```

Then commit:

```bash
git commit -m "Remove old file"
```

---

# 25. Rename Files

```bash
git mv old-name.txt new-name.txt
```

Then commit:

```bash
git commit -m "Rename file"
```

---

# 26. See Who Changed a Line

```bash
git blame filename
```

Example:

```bash
git blame index.js
```

Shows which commit and author last modified each line.

---

# 27. Remove a File from Git but Keep It Locally

```bash
git rm --cached filename
```

Useful when you accidentally tracked something that should be ignored.

Example:

```bash
git rm --cached .env
```

Then add `.env` to `.gitignore`.

---

# 28. Rename a Branch

Rename the current branch:

```bash
git branch -m new-name
```

Example:

```bash
git branch -m main
```

---

# 29. Set Main Branch

Rename current branch to `main`:

```bash
git branch -M main
```

Then push:

```bash
git push -u origin main
```

---

# 30. Complete GitHub Setup

For a new local project:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

---

# 31. Everyday Git Workflow

When working on an existing project:

```bash
git pull
```

Make your changes.

Then:

```bash
git status
git add .
git commit -m "Describe changes"
git push
```

---

# 32. Useful Quick Commands

| Command                   | Purpose                      |
| ------------------------- | ---------------------------- |
| `git init`                | Create repository            |
| `git clone`               | Download repository          |
| `git status`              | Check repository status      |
| `git add .`               | Stage all changes            |
| `git commit -m "message"` | Save changes                 |
| `git log`                 | View history                 |
| `git branch`              | View branches                |
| `git switch`              | Change branch                |
| `git merge`               | Merge branches               |
| `git remote -v`           | View GitHub connection       |
| `git push`                | Upload commits               |
| `git pull`                | Download + integrate changes |
| `git fetch`               | Download remote information  |
| `git stash`               | Temporarily save changes     |
| `git restore`             | Undo file changes            |
| `git reset`               | Move HEAD / undo commits     |
| `git diff`                | See changes                  |
| `git tag`                 | Manage versions              |
| `git rm`                  | Remove tracked file          |
| `git mv`                  | Rename tracked file          |

---

# 33. Most Important Commands to Remember

If you forget everything else, remember these:

```bash
git status
git add .
git commit -m "message"
git push
git pull
```

### Basic cycle

```text
CHANGE FILES
     ↓
git status
     ↓
git add .
     ↓
git commit -m "message"
     ↓
git push
```

### Before starting work

```bash
git pull
```

### After finishing work

```bash
git status
git add .
git commit -m "Describe your changes"
git push
```

---

# 34. Emergency Reminder

Before using potentially destructive commands such as:

```bash
git reset --hard
git checkout .
git clean
git push --force
```

**STOP and make sure you understand what will be deleted or overwritten.**

When unsure, check:

```bash
git status
```

and:

```bash
git log --oneline
```

---

# Git Mental Model

Think of Git as three main areas:

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
       ↓
   git push
       ↓
GitHub / Remote Repository
```

And to get changes from GitHub:

```text
GitHub / Remote Repository
       ↓
   git pull
       ↓
Local Repository
       ↓
Working Directory
```

---

## End

This file is intended as a quick Git reference.

When you forget a command, come back here first.
