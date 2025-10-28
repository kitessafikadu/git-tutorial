# 🧠 Comprehensive Git Command Guide

## 🧩 1. Setup and Configuration
Git must know who you are before making commits. These details are stored globally or per repository.

| Command | Description |
|----------|-------------|
| `git config --global user.name "Your Name"` | Sets your username for all repositories. Use `--local` to apply to only one repo. |
| `git config --global user.email "you@example.com"` | Sets your email, which appears in commit metadata. |
| `git config --list` | Displays all current configurations. Helpful for debugging settings. |
| `git config --global core.editor "code --wait"` | Sets Visual Studio Code as your default Git editor. |

💡 **Tip:** Use `git config --show-origin` to see where a config value comes from (global, local, or system).

---

## 📁 2. Starting a Repository
Git can start tracking files in a project by initializing or cloning a repo.

| Command | Description |
|----------|-------------|
| `git init` | Creates a new, empty Git repository in your current directory. Adds a `.git` folder for version tracking. |
| `git clone <repo-url>` | Copies an existing remote repository to your local machine. Great for contributing to others' projects. |

💡 **Tip:** Cloning includes the entire history of the project — not just the latest snapshot.

---

## 💾 3. Recording Changes
Git tracks changes in three areas: **working directory**, **staging area**, and **repository**.

| Command | Description |
|----------|-------------|
| `git status` | Shows which files are staged, modified, or untracked. |
| `git add <file>` | Adds a specific file to the staging area, preparing it for commit. |
| `git add .` | Stages all changed and new files in the current directory. |
| `git commit -m "message"` | Saves staged changes with a descriptive message. |
| `git commit -am "message"` | Adds and commits all **tracked** files (skips new untracked ones). |
| `git diff` | Displays differences between working directory and staging area. |
| `git diff --staged` | Shows differences between staging area and last commit. |

💡 **Tip:** Always write meaningful commit messages — it makes collaboration and debugging much easier.

---

## 🔄 4. Undoing Changes
Mistakes happen! Git gives several ways to undo changes, depending on what you need.

| Command | Description |
|----------|-------------|
| `git restore <file>` | Restores a file in the working directory to the last commit. |
| `git reset <file>` | Unstages a file (moves it from staging area back to working directory). |
| `git reset --soft HEAD~1` | Undo the last commit, but keep changes staged. Useful when you forgot to include a file. |
| `git reset --mixed HEAD~1` | Undo the last commit and unstage changes (keeps them in working directory). |
| `git reset --hard HEAD~1` | Undo the last commit and completely discard all changes. ⚠️ **Irreversible!** |
| `git checkout -- <file>` | Reverts the file to the state of the last commit. |
| `git revert <commit>` | Creates a new commit that reverses changes made by a specific commit (safe for shared branches). |

💡 **Tip:** Use `git reflog` to recover lost commits even after reset or rebase.

---

## 🌿 5. Branching and Merging
Branches allow you to develop features independently without affecting the main code.

| Command | Description |
|----------|-------------|
| `git branch` | Lists all branches in the repository. The current branch is marked with `*`. |
| `git branch <name>` | Creates a new branch but doesn’t switch to it. |
| `git checkout <name>` | Switches to the specified branch. |
| `git checkout -b <name>` | Creates and switches to a new branch in one step. |
| `git merge <branch>` | Combines another branch into the current one. Creates a merge commit. |
| `git branch -d <name>` | Deletes a branch (only if it’s been merged). |
| `git branch -D <name>` | Force deletes a branch (even if unmerged). |
| `git switch <branch>` | A modern alternative to `git checkout` for switching branches. |
| `git switch -c <branch>` | Creates and switches to a new branch in one go. |

💡 **Tip:** Use branching to isolate features, bug fixes, or experiments.

---

## 🧮 6. Rebasing
Rebasing is used to **reapply commits** from one branch onto another, resulting in a cleaner, linear history.

| Command | Description |
|----------|-------------|
| `git rebase <branch>` | Reapplies commits of current branch onto `<branch>`. |
| `git rebase -i HEAD~n` | Opens interactive mode to reorder, squash, or edit commits. |
| `git rebase --abort` | Cancels the current rebase process. |
| `git rebase --continue` | Continues rebase after fixing merge conflicts. |

💡 **Tip:** Use `rebase` for local feature branches before merging into main to maintain a clean history.

---

## 📤 7. Working with Remotes
Remote repositories (like GitHub) let teams collaborate easily.

| Command | Description |
|----------|-------------|
| `git remote -v` | Shows linked remote repositories and their URLs. |
| `git remote add origin <url>` | Adds a new remote repository. |
| `git fetch` | Downloads commits, branches, and tags without merging. |
| `git pull` | Fetches and merges changes from remote branch. |
| `git pull --rebase` | Fetches and rebases your commits on top of the remote branch. |
| `git push` | Uploads your local commits to the remote branch. |
| `git push -u origin <branch>` | Pushes a branch and sets it as the default upstream for future pushes. |
| `git push origin --delete <branch>` | Deletes a branch on the remote repository. |

💡 **Tip:** Always pull before pushing to avoid conflicts.

---

## 🧱 8. Stashing (Temporary Save)
Use stash when you want to save your current work temporarily without committing.

| Command | Description |
|----------|-------------|
| `git stash` | Saves your modified files and restores a clean working directory. |
| `git stash save "message"` | Saves your changes with a custom message. |
| `git stash list` | Displays all saved stashes. |
| `git stash apply` | Reapplies the most recent stash. |
| `git stash apply stash@{n}` | Applies a specific stash by index. |
| `git stash drop stash@{n}` | Deletes a particular stash. |
| `git stash clear` | Removes all stashes. |

💡 **Example:** You're halfway through a feature but need to switch branches quickly — stash your work first!

---

## 🧭 9. Viewing History
Git keeps a full history of every change ever made.

| Command | Description |
|----------|-------------|
| `git log` | Shows full commit history with author, date, and message. |
| `git log --oneline` | Displays a compact view of commits. |
| `git log --graph --oneline --all` | Shows branch structure visually. |
| `git show <commit>` | Displays details of a specific commit. |
| `git blame <file>` | Shows who last modified each line in a file. |

💡 **Tip:** Use `git log --stat` to see which files were changed in each commit.

---

## 🧹 10. Cleaning Up
Clean up untracked files or directories safely.

| Command | Description |
|----------|-------------|
| `git clean -n` | Shows what files would be deleted (safe dry run). |
| `git clean -f` | Deletes untracked files. |
| `git clean -fd` | Deletes untracked files and directories. |

💡 **Tip:** Always use `-n` before running `-f` to avoid deleting important files.

---

## 🧰 11. Tagging
Tags mark important points in your repository, such as release versions.

| Command | Description |
|----------|-------------|
| `git tag` | Lists all tags. |
| `git tag <name>` | Creates a lightweight tag (simple label). |
| `git tag -a <name> -m "message"` | Creates an annotated tag with a message and metadata. |
| `git push origin <tag>` | Pushes a specific tag to the remote. |
| `git push origin --tags` | Pushes all tags to the remote. |
| `git tag -d <name>` | Deletes a local tag. |

💡 **Tip:** Tags are great for marking releases like `v1.0`, `v2.0`, etc.

---

## ⚙️ 12. Collaboration Tips
These are commands you'll frequently use when working in a team.

| Command | Description |
|----------|-------------|
| `git fetch origin main` | Fetches latest commits from the main branch. |
| `git merge origin/main` | Merges the latest main changes into your branch. |
| `git rebase origin/main` | Rebases your commits on top of main for a cleaner history. |
| `git cherry-pick <commit>` | Applies a specific commit from another branch to current one. |

💡 **Tip:** Rebase before merging your feature branch to avoid unnecessary merge commits.

---

## 🚑 13. Common Fix Commands
These help you recover or fix common mistakes.

| Command | Description |
|----------|-------------|
| `git merge --abort` | Cancels a merge in progress. |
| `git rebase --abort` | Cancels an ongoing rebase. |
| `git reflog` | Shows a log of all actions (useful to recover lost commits). |
| `git restore --staged <file>` | Unstages a file but keeps changes. |
| `git rm --cached <file>` | Removes file from staging area without deleting it locally. |

💡 **Example:** If you accidentally staged `.env`, use `git rm --cached .env` to unstage it and then add it to `.gitignore`.

---

### 💡 Bonus Tips:
- Use `git alias` to create shortcuts for common commands. Example: `git config --global alias.st status`.
- Run `git help <command>` or `<command> --help` to see detailed usage info.
- Combine commands with `&&` to chain actions:
  ```bash
  git add . && git commit -m "Update UI" && git push origin main
  ```

---

✨ **With these commands and explanations, you’ll be able to manage, collaborate, and recover in Git like a pro.**

