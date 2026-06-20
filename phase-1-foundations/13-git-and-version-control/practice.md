# Git and Version Control

> Imagine spending 3 months building a Machine Learning project.
>
> One day, you accidentally delete an important file.
>
> Or you make a change that breaks everything.
>
> Or you want to go back to how the project looked last week.
>
> Without Version Control, this can become a nightmare.
>
> Git solves this problem.
>
> Git is one of the most important tools every software engineer, data scientist, and AI engineer must know.

---

# What is Version Control?

Version Control is a system that tracks changes made to files over time.

Think of it like:

```text id="w71jk8"
Google Docs Version History
```

or

```text id="n8fhwp"
Game Save Points
```

It allows you to:

* Track changes
* Restore older versions
* Collaborate with others
* Experiment safely

---

# Why Do We Need Version Control?

Suppose you have a project:

```text id="vxxqf5"
house_price_prediction.py
```

You make changes.

Now the program stops working.

Without Version Control:

```text id="prcn7n"
No easy way to go back.
```

With Git:

```text id="z6oczw"
Restore previous version instantly.
```

---

# What is Git?

Git is a Version Control System (VCS).

Created by:

Linus Torvalds

Git tracks changes in files and folders.

It remembers:

```text id="92r23o"
Who changed what

When it was changed

Why it was changed
```

---

# What is GitHub?

Git and GitHub are different.

---

## Git

Tool installed on your computer.

Used for:

```text id="mb4qnt"
Version Control
```

---

## GitHub

A cloud platform that stores Git repositories online.

Used for:

* Backup
* Collaboration
* Open Source Projects
* Portfolio Building

---

Simple comparison:

```text id="57hktx"
Git
=
Version Control Tool

GitHub
=
Website that stores Git repositories
```

---

# Repository (Repo)

A repository is simply a project tracked by Git.

Example:

```text id="c9hk5e"
AI-ML-Roadmap/
```

Inside:

```text id="n7wd0j"
README.md

python/

numpy/

pandas/

machine_learning/
```

This entire project can be a repository.

---

# Installing Git

Check installation:

```bash id="o3vh7v"
git --version
```

Example output:

```text id="t9od8m"
git version 2.x.x
```

---

# Initializing a Repository

Navigate to project folder:

```bash id="zjlwmn"
cd my-project
```

Initialize Git:

```bash id="8rnrwe"
git init
```

Output:

```text id="6lqivx"
Initialized empty Git repository
```

Now Git starts tracking the project.

---

# Git Workflow

The basic workflow is:

```text id="mdv4je"
Create File
     ↓
Stage Changes
     ↓
Commit Changes
     ↓
Push to GitHub
```

This cycle repeats throughout development.

---

# Understanding Git States

Git tracks files in three stages:

```text id="o6gzbl"
Working Directory
       ↓
Staging Area
       ↓
Repository
```

---

# Working Directory

Files you're currently editing.

Example:

```text id="6r1t2u"
linear_regression.md
```

You make changes.

Git sees:

```text id="aqj0lp"
File modified
```

---

# Staging Area

Temporary area before committing.

Think:

```text id="0umz40"
Shopping Cart
```

You choose what should be included.

---

# Repository

Permanent saved history.

Think:

```text id="z9jcb4"
Save Point
```

---

# Checking Status

Most used Git command:

```bash id="jlwm9s"
git status
```

Shows:

* Modified files
* New files
* Deleted files
* Staged files

---

# Adding Files

Add one file:

```bash id="8xgy6m"
git add README.md
```

---

Add all files:

```bash id="twjdhx"
git add .
```

Meaning:

```text id="omwrh2"
Stage everything
```

---

# Commit

A commit is a snapshot of your project.

Think:

```text id="1cceiq"
Save Game
```

---

Create commit:

```bash id="e5w2d6"
git commit -m "Added Linear Regression notes"
```

---

Meaning:

```text id="44p3en"
Take snapshot

Attach message
```

---

# Why Commit Messages Matter

Bad:

```bash id="0z70ql"
git commit -m "update"
```

---

Good:

```bash id="afncrh"
git commit -m "Added Random Forest tutorial"
```

Good messages help understand history.

---

# Viewing Commit History

```bash id="v0w5az"
git log
```

Shows:

* Commit ID
* Author
* Date
* Message

---

Example:

```text id="m0l7l9"
Added Python Fundamentals

Added NumPy Guide

Added Pandas Guide
```

---

# Ignoring Files

Some files should not be tracked.

Example:

```text id="2s9hki"
venv/

node_modules/

__pycache__/
```

Create:

```text id="0qvbf8"
.gitignore
```

Example:

```text id="xfljcl"
venv/

__pycache__/

*.log
```

Git ignores them.

---

# What is GitHub?

GitHub stores repositories online.

Benefits:

* Backup
* Collaboration
* Portfolio
* Open Source

---

# Connecting to GitHub

Add remote repository:

```bash id="1m6twt"
git remote add origin <repository-url>
```

Example:

```bash id="2htoqz"
git remote add origin https://github.com/user/project.git
```

---

# Push Changes

Upload commits to GitHub.

```bash id="bnjlwm"
git push origin main
```

Meaning:

```text id="00wk55"
Local Repository
      ↓
GitHub
```

---

# Pull Changes

Download updates.

```bash id="jlwm6h"
git pull origin main
```

Meaning:

```text id="wz9g5r"
GitHub
     ↓
Local Machine
```

---

# Clone Repository

Copy existing repository.

```bash id="iww0nf"
git clone <repository-url>
```

Example:

```bash id="n2onmu"
git clone https://github.com/user/project.git
```

Creates local copy.

---

# Branches

One of Git's most powerful features.

---

# Why Branches Exist

Suppose project is working perfectly.

You want to experiment.

Without branches:

```text id="65ch8w"
Risk breaking everything
```

With branches:

```text id="3e7r0v"
Experiment safely
```

---

# Creating Branch

```bash id="4g3vuw"
git branch feature-login
```

---

Switch Branch

```bash id="kb5bgk"
git checkout feature-login
```

---

Modern shortcut:

```bash id="l14s2f"
git switch feature-login
```

---

Create and Switch

```bash id="sxdl0y"
git checkout -b feature-login
```

---

# Viewing Branches

```bash id="yp4xrr"
git branch
```

Output:

```text id="r0cnx8"
main

feature-login
```

Current branch marked with:

```text id="6k7nhf"
*
```

---

# Merging Branches

Suppose:

```text id="2rx9wp"
feature-login
```

is finished.

Merge into main:

```bash id="e4iv0t"
git merge feature-login
```

Changes become part of main.

---

# Merge Conflict

Occurs when two people modify the same code.

Example:

Person A:

```python id="0h5l5x"
print("Hello")
```

Person B:

```python id="l6mnv4"
print("Hi")
```

Git doesn't know which version to keep.

Manual resolution required.

---

# Undoing Changes

---

# Restore File

```bash id="4dc9gb"
git restore file.py
```

Discard changes.

---

# Reset Staging

```bash id="tljlwm"
git reset file.py
```

Remove from staging area.

---

# Reverting Commits

Undo a commit safely.

```bash id="e9yc3h"
git revert <commit-id>
```

Creates a new commit that reverses changes.

---

# Git Workflow Example

Suppose you add:

```text id="zt9j9r"
logistic_regression.md
```

---

Check status:

```bash id="7c4w2h"
git status
```

---

Stage:

```bash id="htxfth"
git add .
```

---

Commit:

```bash id="9jlwmg"
git commit -m "Added Logistic Regression notes"
```

---

Push:

```bash id="qahk98"
git push origin main
```

Done.

---

# Git for AI/ML Projects

Example project:

```text id="i9y5zh"
AI-ML-Roadmap/
```

Git tracks:

```text id="mzcnpw"
Python Code

Jupyter Notebooks

Datasets

Documentation

Experiments
```

---

Useful when:

* Testing new models
* Comparing experiments
* Collaborating
* Building portfolio projects

---

# Common Git Commands

Check Status:

```bash id="0uqwlp"
git status
```

---

Initialize Repository:

```bash id="esu3sd"
git init
```

---

Add Files:

```bash id="qz1q1r"
git add .
```

---

Commit:

```bash id="db4jcn"
git commit -m "message"
```

---

View History:

```bash id="sk4c22"
git log
```

---

Create Branch:

```bash id="nfr10w"
git branch branch-name
```

---

Switch Branch:

```bash id="oxtf0n"
git checkout branch-name
```

---

Merge Branch:

```bash id="7oy7o7"
git merge branch-name
```

---

Push:

```bash id="kwqq7x"
git push origin main
```

---

Pull:

```bash id="6mfj40"
git pull origin main
```

---

Clone:

```bash id="8uzp2v"
git clone url
```

---

# Common Beginner Mistakes

---

## Forgetting to Commit Frequently

Bad:

```text id="vl9f5s"
100 changes

1 commit
```

---

Better:

```text id="16fhfi"
Small changes

Frequent commits
```

---

## Poor Commit Messages

Bad:

```text id="96t4hk"
update
```

---

Good:

```text id="uh3q9p"
Added Gradient Boosting tutorial
```

---

## Working Directly on Main

Safer:

```text id="xwl9l9"
Create branch

Test changes

Merge later
```

---

## Ignoring .gitignore

Can accidentally upload:

* Large files
* Credentials
* Virtual environments

---

# Interview Questions

---

## What is Git?

A distributed version control system.

---

## Difference Between Git and GitHub?

Git:

Version control tool.

GitHub:

Cloud platform hosting Git repositories.

---

## What is a Commit?

A snapshot of project changes.

---

## What is a Branch?

An independent line of development.

---

## What is Merge?

Combining changes from different branches.

---

## What is a Merge Conflict?

When Git cannot automatically combine changes.

---

## What is .gitignore?

A file specifying what Git should not track.

---

# Key Takeaways

1. Git is a version control system.
2. Git tracks project history.
3. Repositories store project files and history.
4. Commits are project snapshots.
5. GitHub hosts repositories online.
6. Branches allow safe experimentation.
7. Merging combines work from different branches.
8. `.gitignore` prevents unwanted files from being tracked.
9. Git is essential for software engineering and AI projects.
10. Learning Git early will save countless hours later.

---

# Final Mental Model

```text id="iw7s9w"
Create File
     ↓
Modify File
     ↓
git add
     ↓
git commit
     ↓
git push
     ↓
GitHub
```

Think of Git as:

```text id="qytl2w"
A Time Machine
for your code.
```

It remembers every important change and allows you to go back whenever needed.
