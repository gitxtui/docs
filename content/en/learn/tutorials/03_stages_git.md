---
title: The Three Stages in Git
weight: 3
type: "docs"
---

## What Are the Three Stages in Git?

Git tracks your changes in three main stages:  
**Working Directory**, **Staging Area (Index)**, and **Repository (Commit History)**.  
Understanding these stages is key to mastering Git’s workflow!

---

## 1. Working Directory

- This is your project folder on your computer.
- Any changes you make to files—editing, adding, deleting—happen here first.
- Files in the working directory can be:
  - **Untracked:** New files Git hasn’t seen before.
  - **Modified:** Files you’ve changed since the last commit.

**Example:**  
You edit `main.py` and add a new file `README.md`.  
Both are in your working directory.

---

## 2. Staging Area (Index)

- The **staging area** is a place where you tell Git which changes you want to include in your next commit.
- You move changes from the working directory to the staging area using:
```bash
git add <filename>
```
- Only staged changes will be included in your next commit.

**Example:**  
You want to commit only changes to `main.py`, not `README.md` yet:
```bash
git add main.py
```
Now, `main.py` is staged, but `README.md` is not.

---

## 3. Repository (Commit History)

- The **repository** is where Git permanently stores your project’s history.
- When you commit, all staged changes are saved as a new snapshot (commit) in the repository.
- Commits are safe, versioned, and can be shared with others.

**Example:**  
You commit your staged changes:
```bash
git commit -m "Update main.py with new feature"
```
Now, your changes to `main.py` are part of the repository history.

---

## Visual Summary

```
[Working Directory] --(git add)--> [Staging Area] --(git commit)--> [Repository]
```

- **Working Directory:** Where you edit files.
- **Staging Area:** Where you prepare changes for commit.
- **Repository:** Where your project’s history lives.

---

## Why Are These Stages Important?

- **Control:**  
  You choose exactly which changes to commit.
- **Safety:**  
  Only committed changes are saved in history; you can undo or redo as needed.
- **Collaboration:**  
  Commits can be shared, reviewed, and merged with others.

---

> **Tip:**  
> Use `git status` often to see which files are untracked, modified, or staged.  
> Mastering the three stages gives you full control over your project’s