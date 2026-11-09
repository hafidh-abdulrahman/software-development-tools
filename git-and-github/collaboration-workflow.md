# Collaborative Development Workflow

This guide follows a realistic example of a small student team using Git and GitHub.

## The Scenario

Three students, **Amina**, **Hafidh**, and **Luca**, are building a Library Management web app for a course project. They share one GitHub repository called `library-app`.

| Person | Task |
|--------|------|
| Amina | Create the book search feature |
| Hafidh | Create the login page |
| Luca | Write documentation and tests |

---

## 1. Setting Up Collaboration

1. The repository owner opens **Settings > Collaborators** and invites teammates by GitHub username.
2. Teammates accept the invitation by email.
3. Each teammate clones the repository:

```bash
git clone https://github.com/<owner>/library-app.git
cd library-app
```

### Protect the main branch (recommended)

In **Settings > Branches**, add a rule for `main` to require a pull request and at least one approval before merging. This keeps the main branch stable.

---

## 2. Feature Branch Workflow

The most beginner-friendly workflow:

1. `main` always contains working code.
2. Each task gets its own **feature branch**.
3. Work is merged back through a **pull request** after review.

```
main      ----o--------o-----------o------->
               \      /  \        /
login-page      o--o--o    \      /
search-feature              o--o-o
```

### Branch naming

Use short descriptive names: `feature/login-page`, `fix/search-crash`, `docs/update-readme`.

---

## 3. Step-by-Step Example (Hafidh builds the login page)

### Step 1: Get the latest code

```bash
git switch main
git pull origin main
```

### Step 2: Create a branch

```bash
git switch -c feature/login-page
```

### Step 3: Make changes and commit often

```bash
# create login.html and edit it
git add login.html
git commit -m "Add login form layout"

# edit again
git add login.html
git commit -m "Add input validation to login form"
```

### Step 4: Push the branch

```bash
git push -u origin feature/login-page
```

GitHub prints a link to open a pull request.

### Step 5: Open a pull request

On GitHub, click **Compare & pull request**, then fill in:

- **Title:** Add login page
- **Description:** What was done, how to test it, and a reference to the issue (for example `Closes #3`).
- **Reviewers:** Assign Amina.

### Step 6: Code review

The reviewer reads the **Files changed** tab and can:

- Leave comments on specific lines.
- **Approve** the pull request.
- **Request changes** if something needs fixing.

If changes are requested, Hafidh commits to the same branch and pushes again. The pull request updates automatically.

```bash
git add login.html
git commit -m "Fix: show error message for empty password"
git push
```

### Step 7: Merge

When approved and automated checks pass, click **Merge pull request**. GitHub options:

| Option | Result |
|--------|--------|
| Create a merge commit | Keeps all branch commits plus a merge commit |
| Squash and merge | Combines all commits into one clean commit |
| Rebase and merge | Replays commits on top of `main` (advanced) |

For beginners, **Squash and merge** or the default merge commit are both fine.

### Step 8: Clean up and sync

```bash
git switch main
git pull origin main                 # get the merged result
git branch -d feature/login-page     # delete local branch
```

GitHub offers a **Delete branch** button for the remote branch after merging.

---

## 4. Resolving a Conflict in a Pull Request

Suppose Amina and Hafidh both edited the page title in `index.html`. Amina's pull request merges first. When Hafidh's pull request is ready, GitHub reports **"This branch has conflicts that must be resolved."**

### Fix locally

```bash
git switch feature/login-page
git fetch origin
git merge origin/main
# CONFLICT (content): Merge conflict in index.html
```

Open `index.html`, find the markers, and choose the correct final content:

```html
<<<<<<< HEAD
<title>Library Login</title>
=======
<title>Library Search</title>
>>>>>>> origin/main
```

Edit to the correct result, for example:

```html
<title>Library System</title>
```

Then finish:

```bash
git add index.html
git commit -m "Resolve merge conflict in index.html"
git push
```

The pull request now shows no conflicts and can be merged.

### Ways to avoid conflicts

- Pull from `main` frequently.
- Keep branches small and short-lived.
- Agree on who edits which files.
- Communicate before changing shared files.

---

## 5. Linking Work to Issues

Reference issue numbers in pull requests and commits:

```
Add login page. Closes #3
```

Keywords such as `Closes`, `Fixes`, and `Resolves` automatically close the issue when the pull request merges into the default branch.

---

## 6. Forking Workflow (Contributing to Others' Projects)

When you do not have write access (for example, an open-source project):

1. **Fork** the repository on GitHub.
2. **Clone** your fork.
3. Add the original as `upstream`:
   ```bash
   git remote add upstream https://github.com/<original-owner>/<repo>.git
   ```
4. Create a branch, commit, and push to your fork.
5. Open a pull request from your fork to the original repository.
6. Keep your fork updated:
   ```bash
   git fetch upstream
   git switch main
   git merge upstream/main
   ```

---

## 7. Good Team Practices

- Write clear commit messages.
- Make small, focused commits.
- Never commit passwords or API keys.
- Review each other's pull requests respectfully and constructively.
- Do not push directly to `main` if the team has agreed on pull requests.
- Use Issues to track who is doing what.

## References

- GitHub flow: https://docs.github.com/en/get-started/using-github/github-flow
- About pull requests: https://docs.github.com/en/pull-requests
- Resolving merge conflicts: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts
- Contributing to a project (forks): https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project
