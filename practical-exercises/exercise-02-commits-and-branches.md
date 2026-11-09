# Exercise 2: Commits, Branches, and Merging

## Objective

Practise making meaningful commits, creating branches, merging, and resolving a merge conflict. Use the `se-tools-practice` repository from Exercise 1.

## Part A: Several Small Commits

```bash
cd se-tools-practice
git pull

echo "Git tracks changes to files." > git-notes.md
git add git-notes.md
git commit -m "Add Git notes file"

echo "A commit is a snapshot of the project." >> git-notes.md
git add git-notes.md
git commit -m "Define commit in notes"

echo "A branch is a separate line of development." >> git-notes.md
git add git-notes.md
git commit -m "Define branch in notes"

git log --oneline
```

## Part B: Create and Merge a Feature Branch

```bash
git switch -c feature/glossary

echo "# Glossary" > glossary.md
echo "- **Repository**: a project and its history" >> glossary.md
echo "- **Merge**: combine changes from two branches" >> glossary.md
git add glossary.md
git commit -m "Add glossary with two terms"

git switch main
ls                       # glossary.md is not here; it only exists on the branch
git merge feature/glossary
ls                       # now it is
git branch -d feature/glossary
git log --oneline --graph --all
```

Because `main` had no new commits, this was a **fast-forward** merge.

## Part C: Create and Resolve a Merge Conflict

Create two branches that edit the same line.

```bash
echo "Course: Software Development Tools" > course.txt
git add course.txt
git commit -m "Add course file"

git switch -c edit-one
echo "Course: Tools for Software Development" > course.txt
git add course.txt
git commit -m "Reword course title on edit-one"

git switch main
git switch -c edit-two
echo "Course: Software Engineering Tools" > course.txt
git add course.txt
git commit -m "Reword course title on edit-two"

git switch main
git merge edit-one      # succeeds (fast-forward)
git merge edit-two      # CONFLICT
```

Run `git status`, then open `course.txt`. You will see:

```
<<<<<<< HEAD
Course: Tools for Software Development
=======
Course: Software Engineering Tools
>>>>>>> edit-two
```

Edit the file so it contains one final line, with the markers removed:

```
Course: Software Development Tools and Practices
```

Finish the merge:

```bash
git add course.txt
git commit -m "Resolve conflict in course title"
git log --oneline --graph --all
git push
```

## Questions

1. Why was the first merge a fast-forward but the second one a conflict?
2. What do the lines `<<<<<<<`, `=======`, and `>>>>>>>` mean?
3. What command would you use to cancel a merge in progress?
4. Why is it useful to work on a branch instead of directly on `main`?

## Expected Output

- Commits for `git-notes.md`, `glossary.md`, and `course.txt` visible in `git log`.
- A merge commit that resolves the conflict.
- Branches `edit-one` and `edit-two` visible in the graph.

## What to Submit

The output of:

```bash
git log --oneline --graph --all
```
