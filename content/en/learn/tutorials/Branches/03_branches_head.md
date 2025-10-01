---
title: Understanding HEAD 
weight: 6
type: "docs"
---

## What is HEAD in Git?

When working with Git, you’ll often hear about something called **HEAD**.  
Think of `HEAD` as a special pointer that tells Git, “This is where you are right now.”

---

## HEAD: Your Current Position

- **HEAD** always points to your current branch.
- That branch, in turn, points to a specific commit (a snapshot of your project).

**Visualization:**

```
HEAD
 ↓
branch (e.g. main)
 ↓
commit (e.g. a1b2c3d)
```

- When you make a new commit, the branch moves forward, and so does HEAD.

---

## How HEAD Moves

- If you switch branches, HEAD moves to point to the new branch.
- If you make a commit, HEAD (via the branch) points to the new commit.

---

## Detached HEAD State

Sometimes, HEAD doesn’t point to a branch, but **directly to a commit**.  
This is called a **detached HEAD**.

### When does this happen?

- When you checkout a specific commit, not a branch:
  ```bash
  git checkout <commit-hash>
  ```
- Now, HEAD points straight to that commit, not to any branch.

**Visualization:**

```
HEAD
 ↓
commit (not attached to any branch)
```

### Why is this important?

- If you make new commits in this state, they’re not attached to any branch.
- If you switch branches, those commits can be lost (unless you create a new branch from here).

---

## Recovering from Detached HEAD

If you accidentally end up in a detached HEAD and want to save your work:

1. **Create a new branch from here:**
   ```bash
   git switch -c my-temporary-branch
   ```
2. Now your work is safe on a branch!

---

## Summary

- **HEAD** is your current position in the repo.
- Normally, HEAD points to a branch, which points to a commit.
- **Detached HEAD** means HEAD points directly to a commit.
- Always create a branch if you want to keep work done in detached HEAD!

---

> **Tip:**  
> You can always check where HEAD is pointing by running:
> ```bash
> git status
> ```