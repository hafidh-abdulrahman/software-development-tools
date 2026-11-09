# Software Development Tools

![CI](https://github.com/hafidh-abdulrahman/software-development-tools/actions/workflows/basic-ci.yml/badge.svg)

Coursework notes and practical exercises on **using development environments, modelling tools, and source-control systems**.

**Author:** hafidh-abdulrahman
**Repository:** https://github.com/hafidh-abdulrahman/software-development-tools

---

## Project Description

Professional software engineers rarely work with just a compiler and a text editor. They manage requirements, design systems with models, write code in powerful IDEs, track changes with version control, and automate checks with continuous integration. This repository collects my beginner-friendly notes and hands-on exercises covering these tools, written for a Computer Science undergraduate course.

## Objectives

- Explain the purpose of requirements management tools such as IBM Rational DOORS, Jira, Jama Connect, and Azure DevOps.
- Describe how modelling tools such as Sparx Enterprise Architect support software design with UML.
- Compare common IDEs (Eclipse, IntelliJ IDEA, NetBeans, Visual Studio, Xcode) and browser-based alternatives.
- Understand source code management concepts: repositories, commits, branches, merges, and pull requests.
- Use Git and GitHub for individual and collaborative development.
- Use GitHub Issues, README files, and GitHub Actions for tracking, documentation, and basic CI.

## Repository Structure

```
software-development-tools/
├── README.md                       Project overview (this file)
├── .gitignore                      Files Git should not track
├── requirements-management/        DOORS, Jira, Jama, Azure DevOps, traceability
├── design-and-modelling/           Enterprise Architect, UML diagrams, alternatives
├── development-environments/       IDE comparison and browser-based tools
├── git-and-github/
│   ├── README.md                   Source control concepts, Git and GitHub intro
│   ├── basic-git-commands.md       Command reference with examples
│   └── collaboration-workflow.md   Branching, pull requests, merge conflicts
├── documentation/                  Issue tracking, README files, CI with GitHub Actions
├── practical-exercises/
│   ├── README.md                   Exercise overview
│   ├── exercise-01-repository-creation.md
│   ├── exercise-02-commits-and-branches.md
│   └── exercise-03-pull-requests.md
└── .github/workflows/basic-ci.yml  Simple CI workflow
```

## Learning Outcomes

After working through this repository, a student should be able to:

1. Write a simple requirement and trace it to design, code, and tests.
2. Choose a suitable modelling tool and draw basic UML diagrams.
3. Select and set up an IDE for a given language and platform.
4. Create a repository, make commits, and work with branches.
5. Open, review, and merge a pull request on GitHub.
6. Resolve a simple merge conflict.
7. Describe how GitHub Actions automatically checks a repository on every push.

## Setup Instructions

1. **Create a GitHub account** at https://github.com/signup and enable two-factor authentication.
2. **Install Git** from https://git-scm.com/downloads and verify it:
   ```bash
   git --version
   ```
3. **Configure Git** with your identity:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```
4. **Install an IDE** (see [development-environments](development-environments/README.md)) or use a browser-based option such as GitHub Codespaces.
5. **Clone this repository:**
   ```bash
   git clone https://github.com/hafidh-abdulrahman/software-development-tools.git
   cd software-development-tools
   ```
6. Start reading from [requirements-management](requirements-management/README.md), or jump to [practical-exercises](practical-exercises/README.md).

## Suggested Reading Order

1. [Requirements Management](requirements-management/README.md)
2. [Design and Modelling](design-and-modelling/README.md)
3. [Development Environments](development-environments/README.md)
4. [Git and GitHub](git-and-github/README.md), then [Basic Git Commands](git-and-github/basic-git-commands.md) and [Collaboration Workflow](git-and-github/collaboration-workflow.md)
5. [Documentation, Issues, and CI](documentation/README.md)
6. [Practical Exercises](practical-exercises/README.md)

## References

- Pro Git book: https://git-scm.com/book
- GitHub Docs: https://docs.github.com
- GitHub Skills (free interactive courses): https://skills.github.com
- OMG UML specification: https://www.omg.org/spec/UML
