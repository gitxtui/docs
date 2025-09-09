---
title: Stashing Changes in Git
weight: 4
---

## What is Stashing?

**Stashing** in Git lets you temporarily save changes in your working directory that you’re not ready to commit.  
It’s like putting your unfinished work in a "drawer" so you can switch branches, pull updates, or do other tasks—then come back and finish later.

---

## Why Use Stash?

- **Switch branches safely:**  
  If you have uncommitted changes but need to switch to another branch, stash lets you save your work without committing.
- **Keep your work-in-progress separate:**  
  Avoid cluttering your commit history with incomplete or experimental changes.
- **Handle emergencies:**  
  If you need to quickly fix something elsewhere, stash your current work and come back to it later.

---

## How Does Stash Work?

When you run `git stash`, Git saves your changes (tracked files, and optionally untracked files) in a special stack.  
Your working directory is then clean, as if you just checked out the branch.

---

## Basic Stash Commands

### 1. Stash Your Changes

```bash
git stash
```
- Saves your changes and resets your working directory to match the last commit.

### 2. List All Stashes

```bash
git stash list
```
- Shows all stashed changes, each with an identifier like `stash@{0}`.

### 3. Apply the Most Recent Stash

```bash
git stash apply
```
- Restores the latest stashed changes, but keeps them in the stash list.

### 4. Apply and Remove the Most Recent Stash

```bash
git stash pop
```
- Restores the latest stashed changes and **removes** them from the stash list.

### 5. Stash Untracked Files Too

```bash
git stash -u
```
- Includes untracked files (files not yet added with `git add`).

### 6. Drop (Delete) a Stash

```bash
git stash drop stash@{0}
```
- Removes a specific stash from the list.

### 7. Clear All Stashes

```bash
git stash clear
```
- Deletes all stashed changes.

---

## Example Workflow

1. You’re working on a feature but need to switch branches:
   ```bash
   git stash
   git checkout main
   ```
2. Do your work on `main`, then return to your feature branch:
   ```bash
   git checkout feature
   git stash pop
   ```
3. Your changes are restored, and you can continue working.

---

## What Gets Stashed?

- **Tracked files:**  
  Changes to files already being tracked by Git.
- **Untracked files:**  
  Only if you use `git stash -u`.
- **Ignored files:**  
  Only if you use `git stash -a`.

---

## When to Use Stash

- Before switching branches with uncommitted changes.
- When you want to pull or merge updates but aren’t ready to commit your work.
- To save experimental changes without committing them.

---

## Caution

- Stashes are stored locally and are not shared with others.
- If you forget about stashed changes, they can pile up—use `git stash list` to check.
- Always apply or pop your stash on the correct branch to avoid confusion.

---

> **Tip:**  
> Stashing is perfect for saving your work-in-progress without cluttering your commit history.  
> Use it whenever you need to quickly switch