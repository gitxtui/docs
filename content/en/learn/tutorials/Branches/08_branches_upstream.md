---
title: Understanding Upstream Branches
weight: 11
type: "docs"
---

## What is an Upstream Branch?

An **upstream branch** in Git is the remote branch that your local branch is "tracking."  
This means your local branch knows which remote branch it should compare itself to when you run commands like `git pull` or `git push`—so you don’t have to specify the remote branch every time.

---

## Why Use Upstream Branches?

- **Convenience:**  
  You can simply run `git pull` or `git push` without extra arguments, and Git knows which remote branch to use.
- **Collaboration:**  
  Keeps your local branch in sync with the team’s shared branch on the remote server.
- **Safety:**  
  Helps prevent mistakes, like pushing to the wrong branch.

---

## How Do You Set an Upstream Branch?

### When Creating a Local Branch from a Remote Branch

If you create a local branch from a remote branch, Git usually sets the upstream automatically:

```bash
git checkout -b my-feature origin/my-feature
```
- Now, `my-feature` (local) tracks `origin/my-feature` (remote).

### Setting or Changing Upstream Manually

You can set or change the upstream branch for your current branch with:

```bash
git branch -u origin/main
```
- This tells Git: “My current branch should track `origin/main`.”

Or, if you want to set it while pushing for the first time:

```bash
git push -u origin my-feature
```
- The `-u` (or `--set-upstream`) flag tells Git to set the upstream branch.

---

## How Do You Know What Your Upstream Branch Is?

To see what upstream branch your current branch is tracking:

```bash
git status
```
- You’ll see something like:  
  `Your branch is up to date with 'origin/main'.`

Or, for more detail:

```bash
git branch -vv
```
- This shows all local branches and their upstream branches.

---

## What Happens When You Pull or Push?

- **git pull**  
  Fetches changes from the upstream branch and merges them into your local branch.
- **git push**  
  Sends your local commits to the upstream branch on the remote.

If you don’t have an upstream branch set, Git will ask you to specify where to push or pull.

---

## Changing or Removing Upstream Branch

- **Change upstream:**
  ```bash
  git branch -u origin/another-branch
  ```
- **Remove upstream:**
  ```bash
  git branch --unset-upstream
  ```

---

> **Tip:**  
> Always check your upstream branch before pushing or pulling, especially if you’re working on multiple features or with