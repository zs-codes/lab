## 1. Repository Setup & Configuration

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git init` | Creates a new Git repository in current directory | ✅ Use for new projects<br>❌ Don't use in existing repo folders |
| `git clone <url>` | Downloads a repository from remote (GitHub, Azure DevOps, etc.) | ✅ First step when joining a project<br>💡 Use `git clone --depth 1` for faster clone (no history) |
| `git config --global user.name "Name"` | Sets your name for commits | ✅ Do this ONCE after installing Git |
| `git config --global user.email "email"` | Sets your email for commits | ✅ Use company email for work projects |
| `git config --list` | Shows all configuration settings | 💡 Check if identity is set correctly |

---

## 2. Daily Workflow Commands

### Checking Status & Changes

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git status` | Shows modified/staged files | ✅ **Use CONSTANTLY** before every commit<br>💡 Your best friend - run it often! |
| `git diff` | Shows unstaged changes (what you modified) | ✅ Review changes before staging<br>💡 `git diff --staged` shows staged changes |
| `git log` | Shows commit history | ✅ `git log --oneline` for compact view<br>💡 `git log --graph --all` for visual branch history |
| `git show <commit>` | Shows details of specific commit | 💡 `git show HEAD` shows last commit |

### Staging & Committing

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git add <file>` | Stages file for commit | ✅ Stage specific files you want to commit |
| `git add .` | Stages ALL changes in current directory | ⚠️ Be careful! Check `git status` first<br>❌ Don't blindly add everything |
| `git add -p` | Interactive staging (choose which changes) | ✅ **BEST PRACTICE** for partial commits<br>💡 Review each change before staging |
| `git commit -m "message"` | Creates commit with message | ✅ **Always write clear messages**<br>❌ Bad: "fixed stuff"<br>✅ Good: "Fix login timeout issue in auth service" |
| `git commit -am "message"` | Stages tracked files + commits | ⚠️ Only works for **already tracked** files<br>❌ Won't add new files |
| `git commit --amend` | Modify last commit | ✅ Fix typos in commit message<br>❌ **NEVER** amend pushed commits! |

---

## 3. Branch Management

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git branch` | Lists all local branches | 💡 Current branch marked with `*` |
| `git branch <name>` | Creates new branch | ✅ Use descriptive names: `feature/login-page`<br>❌ Avoid: `temp`, `test`, `new` |
| `git branch -d <name>` | Deletes branch (safe) | ✅ Clean up merged branches<br>⚠️ Only deletes if merged |
| `git branch -D <name>` | Force deletes branch | ⚠️ Use carefully - deletes unmerged work! |
| `git checkout <branch>` | Switches to branch | ✅ Make sure you committed/stashed changes first |
| `git checkout -b <name>` | Creates AND switches to new branch | ✅ **MOST USED** - faster than separate commands |
| `git switch <branch>` | Switches to branch (newer syntax) | ✅ Clearer than `checkout` (Git 2.23+) |
| `git switch -c <name>` | Creates AND switches (newer syntax) | ✅ Modern alternative to `checkout -b` |

---

## 4. Remote Repository (GitHub/Azure DevOps)

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git remote -v` | Shows configured remotes | 💡 Check where you're pushing/pulling from |
| `git remote add origin <url>` | Adds remote repository | ✅ Done once after `git init` |
| `git fetch` | Downloads changes WITHOUT merging | ✅ **SAFE** - see what's new before merging<br>💡 Best practice before `pull` |
| `git pull` | Downloads + merges changes | ⚠️ Can cause conflicts<br>✅ Run on clean working directory |
| `git pull --rebase` | Downloads + rebases your commits | ✅ Keeps cleaner history<br>💡 Preferred in team environments |
| `git push` | Uploads your commits | ✅ Push regularly (daily)<br>❌ Don't push broken code to main! |
| `git push -u origin <branch>` | Pushes + sets upstream tracking | ✅ Use FIRST TIME pushing new branch |
| `git push --force` | Overwrites remote history | ❌ **DANGEROUS!** Can lose team's work<br>⚠️ Only use on YOUR branches |

---

## 5. Merging & Rebasing

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git merge <branch>` | Merges branch into current branch | ✅ Example: `git checkout main` → `git merge feature-a`<br>💡 Creates merge commit |
| `git merge --no-ff <branch>` | Forces merge commit (even if fast-forward) | ✅ Better for tracking feature history |
| `git rebase <branch>` | Replays commits on top of another branch | ✅ Keeps linear history<br>❌ **NEVER** rebase pushed commits! |
| `git rebase -i HEAD~3` | Interactive rebase (edit last 3 commits) | ✅ Clean up commits before pushing<br>💡 Squash/reword/reorder commits |

---

## 6. Undoing Changes

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git restore <file>` | Discards unstaged changes | ✅ Undo modifications to file<br>⚠️ **PERMANENTLY DELETES** changes! |
| `git restore --staged <file>` | Unstages file (keeps changes) | ✅ Opposite of `git add` |
| `git reset HEAD~1` | Undo last commit (keeps changes) | ✅ Made commit too early? Use this |
| `git reset --hard HEAD~1` | Undo last commit + delete changes | ❌ **DANGEROUS!** Permanently deletes work |
| `git reset --hard origin/main` | Reset to remote version | ⚠️ Nuclear option - discards ALL local changes |
| `git revert <commit>` | Creates new commit that undoes changes | ✅ **SAFEST** way to undo pushed commits<br>💡 Doesn't rewrite history |

---

## 7. Stashing (Temporary Save)

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git stash` | Saves changes temporarily | ✅ Need to switch branches but not ready to commit?<br>💡 Quick context switching |
| `git stash -u` | Stashes including untracked files | ✅ Includes new files you created |
| `git stash list` | Shows all stashes | 💡 Stashes are numbered: `stash@{0}`, `stash@{1}` |
| `git stash pop` | Applies + deletes most recent stash | ✅ Return to your work |
| `git stash apply` | Applies stash but keeps it in list | 💡 Use if you want to apply to multiple branches |
| `git stash drop` | Deletes a stash | 💡 Clean up old stashes |

---

## 8. Viewing History & Debugging

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git log --oneline` | Compact commit history | ✅ Quick overview |
| `git log --graph --all` | Visual branch history | ✅ See branch relationships |
| `git log -p <file>` | Shows commit history with changes | 💡 Track file evolution |
| `git blame <file>` | Shows who changed each line | ✅ "Who wrote this code?"<br>💡 Not about blame, about context! |
| `git bisect` | Binary search for bug-introducing commit | ✅ Advanced: find which commit broke things |

---

## 9. Tags (Releases/Versions)

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git tag v1.0.0` | Creates lightweight tag | ✅ Mark releases |
| `git tag -a v1.0.0 -m "Release 1.0"` | Creates annotated tag | ✅ **PREFERRED** - includes message & date |
| `git push origin v1.0.0` | Pushes specific tag | 💡 Tags aren't pushed by default! |
| `git push --tags` | Pushes all tags | ✅ Deploy all version tags |

---

## 10. Collaboration Best Practices

| Command | Explanation | Best Use / Best Practice |
|---------|-------------|--------------------------|
| `git fetch origin` | Check for remote changes | ✅ Do this BEFORE starting work each day |
| `git pull origin main` | Update your main branch | ✅ Keep main branch up-to-date |
| `git push origin feature-name` | Push your feature branch | ✅ Push frequently for backup |

---

## Real-World DevOps Workflow Example

```bash
# 1. Start your day - update main
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b feature/azure-devops-agent-setup

# 3. Make changes, check status often
# ... edit files ...
git status                    # See what changed
git diff                      # Review changes

# 4. Stage and commit
git add azure-pipelines.yml
git commit -m "Add Linux self-hosted agent configuration"

# 5. Push to remote
git push -u origin feature/azure-devops-agent-setup

# 6. After PR approved and merged, clean up
git checkout main
git pull origin main
git branch -d feature/azure-devops-agent-setup

# 7. If you need to switch context mid-work
git stash                     # Save current work
git checkout hotfix-bug-123   # Fix urgent bug
# ... fix and commit ...
git checkout feature/azure-devops-agent-setup
git stash pop                 # Continue where you left off
```

---

## Git Message Best Practices

### ✅ Good Commit Messages
```
Fix authentication timeout in Azure AD integration
Add deployment script for production environment
Update documentation for self-hosted agents
Refactor error handling in login service
```

### ❌ Bad Commit Messages
```
fixed stuff
WIP
asdf
update
changes
```

### 📝 Format Template
```
<type>: <short description>

<optional detailed explanation>

<optional issue reference>
```

**Types**: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

---

## Emergency Cheat Sheet

| Situation | Command |
|-----------|---------|
| "I need to undo my last commit" | `git reset HEAD~1` |
| "I want to discard all local changes" | `git restore .` |
| "I committed to wrong branch" | `git reset HEAD~1` then `git checkout correct-branch` |
| "I need to quickly save work and switch branches" | `git stash` |
| "Someone updated main, I need latest" | `git checkout main && git pull` |
| "I want to see what changed" | `git status` then `git diff` |
| "Delete a branch" | `git branch -d branch-name` |

---

## Pro Tips 💡

1. **Commit often**: Small commits > one giant commit
2. **Pull before push**: Avoid conflicts
3. **Use branches**: Never work directly on `main`
4. **Check status**: Run `git status` obsessively
5. **Write clear messages**: Future you will thank you
6. **Backup your work**: Push to remote regularly