# # Git Cheat Sheet

## 1. Setup & Configuration
- **Set user name**: `git config --global user.name "Your Name"`
- **Set user email**: `git config --global user.email "your.email@example.com"`
- **Check config**: `git config --list`
- **Set default editor**: `git config --global core.editor "vim"`
- **Enable color output**: `git config --global color.ui auto`

---

## 2. Repository Initialization
- **Initialize a new repository**: `git init`
- **Clone an existing repository**: `git clone <repo-url>`

---

## 3. Staging & Committing Changes
- **Check status**: `git status`
- **Add a file to staging**: `git add <file>`
- **Add all files to staging**: `git add .`
- **Commit changes**: `git commit -m "commit message"`
- **Amend last commit**: `git commit --amend`

---

## 4. Branching & Merging
- **List branches**: `git branch`
- **Create a new branch**: `git branch <branch-name>`
- **Switch to a branch**: `git checkout <branch-name>`
- **Create and switch to a new branch**: `git checkout -b <branch-name>`
- **Merge a branch**: `git merge <branch-name>`
- **Delete a branch**: `git branch -d <branch-name>`

---

## 5. Remote Repositories
- **Add a remote repository**: `git remote add origin <repo-url>`
- **View remote URLs**: `git remote -v`
- **Fetch from remote**: `git fetch origin`
- **Push to remote**: `git push origin <branch-name>`
- **Pull from remote**: `git pull origin <branch-name>`
- **Remove remote**: `git remote remove origin`

---

## 6. Undoing Changes
- **Unstage a file**: `git reset <file>`
- **Reset last commit (soft)**: `git reset --soft HEAD~1`
- **Reset last commit (hard)**: `git reset --hard HEAD~1`
- **Revert a commit**: `git revert <commit-hash>`
- **Discard changes in working directory**: `git checkout -- <file>`

---

## 7. Stashing Changes
- **Save changes for later**: `git stash`
- **List stashes**: `git stash list`
- **Apply last stash**: `git stash apply`
- **Apply and delete last stash**: `git stash pop`
- **Delete a specific stash**: `git stash drop stash@{n}`

---

## 8. Git Log & History
- **View commit history**: `git log`
- **View history as one line**: `git log --oneline`
- **View commit diff**: `git diff <commit-hash>`
- **Show who changed what**: `git blame <file>`

---

## 9. Setting up a Repository on GitHub
1. **Create a repository on GitHub**
2. **Initialize a local repo**: `git init`
3. **Add files**: `git add .`
4. **Commit files**: `git commit -m "Initial commit"`
5. **Connect to GitHub**: `git remote add origin <repo-url>`
6. **Push code to GitHub**: `git push -u origin main`

---

## 10. Advanced Git Commands
- **Show current branch**: `git rev-parse --abbrev-ref HEAD`
- **Create alias**: `git config --global alias.st status`
- **Squash commits**: `git rebase -i HEAD~n`
- **Find a bug (bisect)**: `git bisect start`
- **Clean untracked files**: `git clean -f`

---

This cheat sheet covers all essential Git commands to help you manage repositories efficiently! 🚀
