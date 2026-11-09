# Exercise 1: Creating and Cloning a Repository

## Objective

Create a GitHub repository, clone it to your computer, make your first commit, and push it back.

## Part A: Verify Your Setup

```bash
git --version
git config --global user.name
git config --global user.email
```

If name or email is blank, set them:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## Part B: Create the Repository on GitHub

1. Sign in to GitHub and click **+ > New repository**.
2. Repository name: `se-tools-practice`.
3. Description: *Practice repository for software development tools.*
4. Choose **Public** (or as your instructor directs).
5. Tick **Add a README file**.
6. Choose the **Python** (or your language's) `.gitignore` template.
7. Click **Create repository**.

## Part C: Clone It

Click **Code**, copy the HTTPS URL, then run:

```bash
git clone https://github.com/<your-username>/se-tools-practice.git
cd se-tools-practice
ls
```

You should see `README.md` and `.gitignore`.

## Part D: First Commit and Push

```bash
echo "# Exercise 1 Notes" > notes.md
echo "I created my first repository on $(date +%F)." >> notes.md

git status
git add notes.md
git commit -m "Add exercise 1 notes"
git push
```

Refresh the repository page on GitHub. `notes.md` should appear.

## Part E: Inspect the History

```bash
git log --oneline
git remote -v
```

## Questions

1. What is the difference between `git clone` and `git init`?
2. Why must you run `git add` before `git commit`?
3. What does `origin` refer to?
4. What happens if you run `git push` before making any commit?

## Expected Output

- A repository named `se-tools-practice` containing `README.md`, `.gitignore`, and `notes.md`.
- At least two commits (the initial commit and your notes commit).

## What to Submit

The URL of your repository, for example `https://github.com/<your-username>/se-tools-practice`.

## Troubleshooting

| Problem | Likely fix |
|---------|-----------|
| `Authentication failed` on push | Use a personal access token instead of your password, or run `gh auth login`. See https://docs.github.com/en/authentication |
| `fatal: not a git repository` | You are in the wrong folder. Use `cd se-tools-practice`. |
| `Author identity unknown` | Set `user.name` and `user.email` (Part A). |
