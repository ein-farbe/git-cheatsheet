# Git Command Cheatsheet

## Setup
- `git config --global user.name "Name"` — set name
- `git config --global user.email "you@example.com"` — set email
- `git config --global core.editor "code --wait"` — set editor
- `git config --list` — view config

## Getting Code
- `git clone <url>` — clone repo
- `git init` — create local repo

## Basic Workflow
- `git status` — show status
- `git add <file|dir>` — stage changes
- `git add -A` — stage all changes (including deletions)
- `git commit -m "msg"` — commit staged changes
- `git commit --amend` — amend last commit
- `git diff` — show unstaged changes
- `git diff --staged` — show staged vs HEAD

## Branching & Switching
- `git branch` — list branches
- `git branch <name>` — create branch
- `git switch <branch>` — switch branch (modern)
- `git checkout <branch>` — switch branch (legacy)
- `git switch -c <name>` — create + switch
- `git branch -d <branch>` — delete branch (safe)
- `git branch -D <branch>` — delete branch (force)

## Merging & Rebasing
- `git merge <branch>` — merge into current branch
- `git rebase <branch>` — rebase current onto branch
- `git rebase -i <commit>` — interactive rebase (rewrite history)

## Remote
- `git remote -v` — list remotes
- `git remote add origin <url>` — add remote
- `git fetch` — fetch from remote (no merge)
- `git pull` — fetch + merge (or `--rebase`)
- `git push origin <branch>` — push branch
- `git push -u origin <branch>` — set upstream
- `git push --force-with-lease` — safe force push

## Undo & Recover
- `git restore <file>` — discard unstaged changes (modern)
- `git restore --staged <file>` — unstage file
- `git reset --soft <commit>` — move HEAD, keep index
- `git reset --mixed <commit>` — move HEAD, reset index (default)
- `git reset --hard <commit>` — reset everything (dangerous)
- `git revert <commit>` — create a new commit that undoes a commit
- `git reflog` — find lost commits/HEADs

## Stash
- `git stash` — save working state
- `git stash push -m "msg"` — stash with message
- `git stash list` — list stashes
- `git stash pop` — apply & drop last stash
- `git stash apply stash@{1}` — apply specific stash

## Inspecting History
- `git log` — commit history
- `git log --oneline --graph --decorate --all` — compact visual log
- `git show <commit>` — show commit details
- `git blame <file>` — see line-by-line commit authorship
- `git bisect start` / `git bisect bad` / `git bisect good` — binary-search bug

## Cherry-pick & Tag
- `git cherry-pick <commit>` — apply commit to current branch
- `git tag <v1.0>` — create lightweight tag
- `git tag -a v1.0 -m "msg"` — annotated tag
- `git push origin v1.0` — push tag

## Submodules
- `git submodule add <url> path` — add submodule
- `git submodule update --init --recursive` — init/update

## Collaboration Helpers
- `git fetch origin` then `git rebase origin/main` — update local branch cleanly
- `git pull --rebase` — rebase local commits on top of remote
- `git format-patch` / `git am` — email-style patch workflow

## Config & Helpers
- `git config --global alias.st status` — create alias
- `git config --global --edit` — edit global config
- `git gc --prune=now --aggressive` — garbage collect

## Safety Tips
- Prefer `--force-with-lease` over `--force`.
- Use `git status` and `git log --oneline --graph` before destructive commands.
- Use `git stash` or a temporary branch before risky operations.

## Quick Examples
### New Feature Flow
1. `git switch -c feature/x`
2. work, `git add` → `git commit -m "..."`
3. `git push -u origin feature/x`
4. open PR, merge into `main`

### Recover Lost Commit
1. `git reflog` → find commit hash
2. `git switch -c recover <hash>`

---

*For bash on macOS. Last updated: 2025-11-03.*
