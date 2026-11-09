# Exercise 3: Pull Requests, Issues, and CI

## Objective

Use the GitHub workflow: create an issue, work on a branch, open a pull request, review it, and merge it. Observe a CI check run.

This exercise works best with a partner, but you can do both roles yourself.

## Part A: Add the CI Workflow

In your `se-tools-practice` repository, create the folder `.github/workflows` and a file `ci.yml`:

```yaml
name: Basic CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Check README exists
        run: test -f README.md && echo "README found"
```

Commit and push it to `main`:

```bash
mkdir -p .github/workflows
# create ci.yml with the content above
git add .github/workflows/ci.yml
git commit -m "Add basic CI workflow"
git push
```

Open the **Actions** tab and confirm the run shows a green tick.

## Part B: Create an Issue

1. Go to **Issues > New issue**.
2. Title: `Add project description to README`.
3. Description: *The README only has a title. Add a short description and a list of the topics covered.*
4. Add the label `documentation` and assign yourself.
5. Submit. Note the issue number, for example `#1`.

## Part C: Work on a Branch

```bash
git switch main
git pull
git switch -c docs/readme-description

# Edit README.md: add a short description and a topic list
git add README.md
git commit -m "Add project description and topics to README"
git push -u origin docs/readme-description
```

## Part D: Open a Pull Request

1. On GitHub, click **Compare & pull request**.
2. Title: `Add project description to README`.
3. Description:

   ```markdown
   ## What changed
   Added a description and topic list to the README.

   ## How to check
   Open README.md and read the new sections.

   Closes #1
   ```

4. If you have a partner, assign them as reviewer.
5. Click **Create pull request**.
6. Wait for the CI check to finish. It should pass.

## Part E: Review

The reviewer (your partner, or you) should:

1. Open the **Files changed** tab.
2. Hover over a line, click **+**, and leave one comment, such as a suggestion to improve wording.
3. Submit the review as **Approve** or **Request changes**.

If changes were requested, the author edits locally and pushes again:

```bash
git add README.md
git commit -m "Address review feedback"
git push
```

## Part F: Merge and Clean Up

1. Click **Merge pull request** (or **Squash and merge**), then **Confirm**.
2. Click **Delete branch**.
3. Notice that issue `#1` closed automatically.
4. Update your local copy:

```bash
git switch main
git pull
git branch -d docs/readme-description
git log --oneline
```

## Questions

1. What is the benefit of a pull request compared with merging locally?
2. How did `Closes #1` affect the issue?
3. What did the CI check verify, and why is that useful before merging?
4. What happens to the pull request if you push another commit to its branch?

## Expected Output

- A closed issue linked to a merged pull request.
- A review comment on the pull request.
- A green CI check on the pull request.
- An updated `main` branch containing the README changes.

## What to Submit

The link to your merged pull request, for example `https://github.com/<your-username>/se-tools-practice/pull/2`.
