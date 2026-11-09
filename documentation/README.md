# Issue Tracking, Documentation, and Continuous Integration

## 1. Issue Tracking

An **issue tracker** is a tool for recording and managing units of work: bugs, new features, questions, and tasks. Each item has a number, a description, a status, and usually an owner.

### Why track issues?

- Nothing gets forgotten; work is visible to the whole team.
- Discussions about a task stay attached to the task.
- Progress can be measured.
- Issues link to code, giving traceability from request to implementation (see [requirements-management](../requirements-management/README.md)).

Other trackers include Jira, Azure DevOps Boards, Trello, and GitLab Issues.

### GitHub Issues

GitHub Issues is built into every repository (the **Issues** tab).

| Feature | Description |
|---------|-------------|
| Title and description | Explain the problem or task, supports Markdown |
| Labels | Categorise, for example `bug`, `enhancement`, `documentation` |
| Assignees | People responsible for the issue |
| Milestones | Group issues for a deadline or release |
| Projects | Kanban-style boards (To do, In progress, Done) |
| Mentions | `@username` notifies a person |
| Cross-references | `#12` links to issue or pull request 12 |

### Creating a good issue

1. Open **Issues > New issue**.
2. Write a clear title: *"Login button does nothing on mobile"*.
3. Describe it:

```markdown
## Description
Tapping the Login button on a phone does not submit the form.

## Steps to reproduce
1. Open the site on a mobile browser.
2. Enter a valid username and password.
3. Tap "Login".

## Expected behaviour
The user is logged in.

## Actual behaviour
Nothing happens.
```

4. Add labels (`bug`) and an assignee.
5. Click **Submit new issue**.

### Closing issues from code

Put a keyword in a pull request description or commit message:

```
Fix login button on mobile. Closes #12
```

When merged into the default branch, issue #12 closes automatically.

---

## 2. Project Documentation

Good documentation helps others (and your future self) understand and use your project.

### Types of documentation

| Type | Audience | Examples |
|------|----------|----------|
| User documentation | End users | Installation guide, tutorials |
| Developer documentation | Other developers | Setup steps, architecture notes, API descriptions |
| Process documentation | The team | Contribution guidelines, branching rules |
| Code comments | Maintainers | Explaining why code does something non-obvious |

### README files

The `README.md` is the front page of a repository. GitHub displays it automatically. It is written in **Markdown**.

A good README contains:

1. **Project title and short description**
2. **Features** or objectives
3. **Installation / setup** instructions
4. **Usage** examples
5. **Project structure**
6. **Contributing** guidelines
7. **Licence**
8. **Contact** or author information

Example skeleton:

```markdown
# Project Name

Short description of what the project does.

## Installation
    git clone https://github.com/user/project.git
    cd project

## Usage
Explain how to run it.

## Contributing
Open an issue or submit a pull request.

## Licence
MIT
```

### Markdown quick reference

| Syntax | Result |
|--------|--------|
| `# Heading` | Large heading (`##`, `###` for smaller) |
| `**bold**` and `*italic*` | **bold** and *italic* |
| `- item` | Bulleted list |
| `1. item` | Numbered list |
| `[text](https://example.com)` | Link |
| `` `code` `` | Inline code |
| Triple backticks | Code block |
| `> quote` | Block quote |

### Other documentation files on GitHub

- `LICENSE`: states how others may use your code.
- `CONTRIBUTING.md`: explains how to contribute.
- `.gitignore`: lists files Git should not track.
- **Wiki** and **GitHub Pages**: for longer documentation sites.

---

## 3. Continuous Integration (CI)

**Continuous Integration** is the practice of merging code changes into a shared branch frequently, with each change **automatically built and tested**.

### Why CI?

- Problems are found within minutes of a push, not weeks later.
- Everyone sees whether `main` is healthy.
- Reduces the "it works on my machine" problem.
- Gives reviewers confidence before approving a pull request.

### A typical CI pipeline

```
Push or pull request  -->  Checkout code  -->  Install dependencies  -->  Build  -->  Run tests  -->  Report pass/fail
```

Related term: **Continuous Delivery/Deployment (CD)** extends CI by automatically releasing the software. It is beyond this course's scope.

---

## 4. GitHub Actions

**GitHub Actions** is GitHub's built-in automation platform. Workflows are defined in YAML files stored in `.github/workflows/`.

### Key terms

| Term | Meaning |
|------|---------|
| Workflow | An automated process defined in one YAML file |
| Event (trigger) | What starts the workflow, such as `push` or `pull_request` |
| Job | A set of steps that run on one machine |
| Runner | The virtual machine that executes a job (for example `ubuntu-latest`) |
| Step | One task: a shell command or a reusable **action** |
| Action | A reusable unit, such as `actions/checkout` |

### The workflow in this repository

See [`.github/workflows/basic-ci.yml`](../.github/workflows/basic-ci.yml). It runs on every push and pull request to `main`, and it:

1. Checks out the repository.
2. Prints the Git version and runner information.
3. Verifies that the required folders and files exist.
4. Checks that no Markdown file is empty.

### Anatomy of a workflow

```yaml
name: Basic CI            # name shown in the Actions tab

on:                       # events that trigger the workflow
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  check:                  # job name
    runs-on: ubuntu-latest   # runner
    steps:
      - uses: actions/checkout@v4   # reusable action
      - name: Say hello
        run: echo "Hello from GitHub Actions"   # shell command
```

### Viewing results

1. Open the repository's **Actions** tab.
2. Select a workflow run to see each job and step.
3. A green tick means all steps passed; a red cross means a step failed. Click it to read the log.

On a pull request, the same status appears near the merge button, so reviewers know whether checks passed.

### Adding a status badge

The badge at the top of the root README is created from this pattern:

```markdown
![CI](https://github.com/<user>/<repo>/actions/workflows/<file>.yml/badge.svg)
```

---

## Key Points

- Issue trackers record and organise work; GitHub Issues links tasks directly to code.
- READMEs and other documentation make a project understandable and usable.
- CI automatically checks every change; GitHub Actions implements CI with YAML workflows.

## References

- About issues: https://docs.github.com/en/issues
- Linking pull requests to issues: https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue
- About READMEs: https://docs.github.com/en/repositories/managing-your-repository-settings-and-features/customizing-your-repository/about-readmes
- Basic writing and formatting syntax: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
- GitHub Actions quickstart: https://docs.github.com/en/actions/quickstart
- Workflow syntax: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions
