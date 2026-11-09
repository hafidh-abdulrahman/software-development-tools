# Basic Git Commands

A practical reference. Every command is explained and followed by an example you can try in a practice folder.

## 1. Setup and Creating Repositories

| Command | What it does |
|---------|--------------|
| `git config --global user.name "Name"` | Sets the name attached to your commits |
| `git config --global user.email "email"` | Sets the email attached to your commits |
| `git init` | Turns the current folder into a new Git repository |
| `git clone <url>` | Copies a remote repository to your computer |

```bash
mkdir demo-project
cd demo-project
git init
# Output: Initialized empty Git repository in .../demo-project/.git/
```

```bash
git clone https://github.com/hafidh-abdulrahman/software-development-tools.git
```

## 2. Checking Status and History

| Command | What it does |
|---------|--------------|
| `git status` | Shows changed, staged, and untracked files |
| `git log` | Shows the full commit history |
| `git log --oneline` | One line per commit (short and readable) |
| `git log --oneline --graph --all` | Shows branches as an ASCII graph |
| `git diff` | Shows unstaged changes line by line |
| `git diff --staged` | Shows changes that are staged for the next commit |
| `git show <commit>` | Shows details of a single commit |

```bash
git status
git log --oneline
```

## 3. Making Commits

| Command | What it does |
|---------|--------------|
| `git add <file>` | Stages one file |
| `git add .` | Stages all changes in the current folder |
| `git commit -m "message"` | Saves the staged changes as a commit |
| `git commit --amend` | Edits the most recent commit (only before pushing) |

### Worked example

```bash
echo "# My Notes" > notes.md          # create a file
git status                            # notes.md is untracked
git add notes.md                      # stage it
git commit -m "Add notes file"        # save the snapshot

echo "Git tracks changes." >> notes.md   # edit the file
git diff                                 # see what changed
git add notes.md
git commit -m "Add first note about Git"
git log --oneline
```

Expected log (hashes will differ):

```
b7c2e91 Add first note about Git
3fa81d4 Add notes file
```

## 4. Undoing Things

| Command | What it does | Safe? |
|---------|--------------|-------|
| `git restore <file>` | Discards unstaged changes to a file | Changes are lost |
| `git restore --staged <file>` | Unstages a file but keeps your edits | Yes |
| `git revert <commit>` | Creates a new commit that undoes an earlier one | Yes, history is preserved |
| `git reset --hard <commit>` | Moves the branch back and discards later work | Dangerous; avoid on shared branches |

```bash
git restore --staged notes.md   # change your mind about staging
git revert HEAD                 # undo the last commit safely
```

## 5. Remotes: Pushing and Pulling

| Command | What it does |
|---------|--------------|
| `git remote -v` | Lists remote repositories |
| `git remote add origin <url>` | Links your local repo to a remote named `origin` |
| `git push -u origin main` | Uploads `main` and remembers it as the default upstream |
| `git push` | Uploads new commits on the current branch |
| `git fetch` | Downloads remote changes without merging them |
| `git pull` | Downloads remote changes and merges them into your branch |

```bash
git remote add origin https://github.com/hafidh-abdulrahman/demo-project.git
git push -u origin main     # first push
# later:
git pull                    # get teammates' changes
git push                    # share yours
```

**Tip:** run `git pull` before starting work each day to reduce conflicts.

## 6. Branching and Merging

| Command | What it does |
|---------|--------------|
| `git branch` | Lists local branches |
| `git branch <name>` | Creates a branch |
| `git switch <name>` | Switches to a branch |
| `git switch -c <name>` | Creates and switches in one step |
| `git merge <name>` | Merges the named branch into the current branch |
| `git branch -d <name>` | Deletes a merged branch |
| `git push origin --delete <name>` | Deletes a remote branch |

```bash
git switch -c feature-about-page      # create and move to new branch
echo "About us" > about.md
git add about.md
git commit -m "Add about page"

git switch main                       # return to main
git merge feature-about-page          # bring the feature in
git branch -d feature-about-page      # clean up
git log --oneline --graph --all
```

### Types of merge

- **Fast-forward**: `main` had no new commits, so Git simply moves the pointer forward.
- **Merge commit**: both branches changed, so Git creates a new commit joining them.

## 7. Resolving Merge Conflicts

A **conflict** happens when two branches change the same lines of a file. Git cannot choose, so it asks you.

### Example

```bash
git switch -c branch-a
echo "Title: Version A" > title.txt
git add title.txt && git commit -m "Set title to A"

git switch main
echo "Title: Version B" > title.txt
git add title.txt && git commit -m "Set title to B"

git merge branch-a
# CONFLICT (add/add): Merge conflict in title.txt
# Automatic merge failed; fix conflicts and then commit the result.
```

Open `title.txt`. Git adds markers:

```
<<<<<<< HEAD
Title: Version B
=======
Title: Version A
>>>>>>> branch-a
```

- Between `<<<<<<< HEAD` and `=======` is **your current branch**.
- Between `=======` and `>>>>>>>` is **the incoming branch**.

Edit the file to the final text you want and delete all three marker lines:

```
Title: Version A and B Combined
```

Then finish the merge:

```bash
git add title.txt
git commit -m "Resolve merge conflict in title.txt"
```

To abandon the merge instead: `git merge --abort`.

## 8. Useful Extras

| Command | What it does |
|---------|--------------|
| `git stash` | Temporarily shelves uncommitted changes |
| `git stash pop` | Brings shelved changes back |
| `git tag v1.0` | Marks a commit (such as a release) with a name |
| `git blame <file>` | Shows who last changed each line |

## 9. Quick Daily Workflow

```bash
git pull                       # 1. update
git switch -c my-feature       # 2. branch
# ...edit files...
git add .                      # 3. stage
git commit -m "Describe change"# 4. commit
git push -u origin my-feature  # 5. publish, then open a pull request
```

## Reference

- Git command reference: https://git-scm.com/docs
- Git cheat sheet: https://education.github.com/git-cheat-sheet-education.pdf
