# Source Code Management, Git, and GitHub

## 1. Source Code Management (SCM)

**Source code management**, also called **version control**, is the practice of tracking and managing changes to files over time. A **version control system (VCS)** records every change so you can see history, compare versions, undo mistakes, and collaborate safely.

### Types of version control systems

| Type | Description | Examples |
|------|-------------|----------|
| Local | History stored only on one computer | RCS |
| Centralised (CVCS) | One central server holds the history | Subversion (SVN), Perforce |
| Distributed (DVCS) | Every developer has a full copy of the history | **Git**, Mercurial |

Distributed systems let you work offline, commit quickly, and keep working even if the server is unavailable.

### Advantages of source code management

- **History**: see who changed what, when, and why.
- **Undo**: return to any earlier version.
- **Collaboration**: many people work on the same project without overwriting each other.
- **Branching**: experiment safely in isolation.
- **Backup**: remote repositories protect against lost laptops.
- **Accountability and traceability**: each change has an author and message.
- **Code review**: changes are inspected before they are merged.

---

## 2. Core Concepts

### Repository (repo)

A project folder together with its complete history. A **local repository** lives on your computer; a **remote repository** lives on a server such as GitHub.

### Commit

A saved snapshot of the project, with a unique ID (hash), an author, a timestamp, and a message.

Good commit messages are short and in the imperative mood:

```
Add login validation
Fix crash when course list is empty
Update README with setup steps
```

### Branch

An independent line of development. The default branch is usually `main`. Branches let you build a feature or fix a bug without affecting stable code.

```
main:      A---B---C-------------G
                    \           /
feature-login:       D---E---F
```

### Merge

Combining the changes from one branch into another. In the diagram above, `feature-login` is merged into `main` to create commit `G`.

### Pull request (PR)

A GitHub feature for **proposing** that your branch be merged. A PR shows the changes, lets teammates comment and approve, and can trigger automated checks before the merge happens.

### Other useful terms

| Term | Meaning |
|------|---------|
| Clone | Copy a remote repository to your computer |
| Fork | Your own copy of someone else's repository on GitHub |
| Remote | A named link to a hosted repository (usually `origin`) |
| Push | Upload local commits to a remote |
| Pull | Download and integrate remote commits |
| Staging area | Where you choose which changes go into the next commit |
| HEAD | Pointer to the commit or branch you are currently on |

---

## 3. Introduction to Git

**Git** is a free, open-source distributed version control system created by Linus Torvalds in 2005 for developing the Linux kernel. It is now the most widely used VCS in the world.

### The three areas of Git

```
Working directory  --git add-->  Staging area  --git commit-->  Local repository  --git push-->  Remote (GitHub)
```

1. **Working directory**: the files you edit.
2. **Staging area**: changes you have selected for the next commit.
3. **Repository**: the permanent history.

### Installing Git

| OS | Method |
|----|--------|
| Windows | Download from https://git-scm.com/download/win (includes Git Bash) |
| macOS | Run `git --version` in Terminal to trigger the install, or `brew install git` |
| Linux (Debian/Ubuntu) | `sudo apt install git` |

Verify the installation:

```bash
git --version
```

### Configuring Git

```bash
git config --global user.name "Hafidh Abdulrahman"      # name on your commits
git config --global user.email "you@example.com"        # email on your commits
git config --global init.defaultBranch main             # default branch name
git config --list                                       # show current settings
```

Use the same email address that is registered with your GitHub account so commits are linked to your profile.

---

## 4. Introduction to GitHub

**GitHub** is a web platform that hosts Git repositories and adds collaboration features:

- Remote repository hosting
- Pull requests and code review
- **Issues** for tracking tasks and bugs
- **GitHub Actions** for automation and CI
- **Projects** boards for planning
- README rendering, wikis, and GitHub Pages
- Permissions and teams

Git is the tool; GitHub is a service built around it. Alternatives include GitLab and Bitbucket.

### Authenticating with GitHub

GitHub no longer accepts account passwords for Git operations over HTTPS. Use one of:

- **Personal access token (PAT)** used in place of a password, or
- **SSH keys**, or
- **GitHub CLI** (`gh auth login`) or Git Credential Manager (installed with Git for Windows).

See https://docs.github.com/en/authentication.

### Creating a repository on GitHub

1. Click **+ > New repository** (top right).
2. Enter a name, for example `software-development-tools`.
3. Choose **Public** or **Private**.
4. Optionally tick **Add a README file** and choose a `.gitignore` template.
5. Click **Create repository**.

### Connecting an existing local project to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/hafidh-abdulrahman/software-development-tools.git
git push -u origin main
```

---

## Further Reading in This Folder

- [basic-git-commands.md](basic-git-commands.md): command reference with practical examples.
- [collaboration-workflow.md](collaboration-workflow.md): branching, pull requests, and merge conflicts.

## References

- Pro Git book (free): https://git-scm.com/book
- Git documentation: https://git-scm.com/doc
- GitHub Docs: https://docs.github.com
- GitHub Skills: https://skills.github.com
