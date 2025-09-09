---
title: Rebasing Branches
linkTitle: Understanding Rebasing
weight: 13
---

## What is Rebasing?

**Rebasing** is a way to move or combine a sequence of commits to a new base commit.  
In simple terms, rebasing lets you "replay" your work from one branch onto another branch, creating a cleaner, linear history.

---

## Why Use Rebase?

- **Cleaner History:**  
  Rebasing creates a straight line of commits, making the project history easier to read.
- **Avoids Merge Commits:**  
  Unlike merging, rebasing doesn’t create extra merge commits unless there are conflicts.
- **Keeps Features Up-to-Date:**  
  You can update your feature branch with the latest changes from `main` before merging.

---

## How Does Rebasing Work?

Imagine you have this history:

```
A---B---C main
         \
          D---E feature
```

If you run `git rebase main` while on `feature`, Git will:

1. Temporarily remove commits `D` and `E` from `feature`.
2. Move `feature` to the tip of `main` (commit `C`).
3. Replay `D` and `E` on top of `C`.

Result:

```
A---B---C---D'---E' feature
```
- `D'` and `E'` are new commits (copies of `D` and `E`).

---

## Basic Rebase Command

```bash
git checkout feature
git rebase main
```
- This moves your `feature` branch to start from the latest commit on `main`.

---

## Interactive Rebase

**Interactive rebase** lets you edit, reorder, squash, or drop commits.

```bash
git rebase -i HEAD~n
```
- Replace `n` with the number of commits you want to edit.
- You’ll see a list of commits in your editor, where you can:
  - `pick` (keep as is)
  - `reword` (edit commit message)
  - `squash` (combine commits)
  - `drop` (remove a commit)

---

## Rebasing vs. Merging

| Action   | Result                                      | History Shape      |
|----------|---------------------------------------------|--------------------|
| Merge    | Combines branches, creates merge commits    | Branched           |
| Rebase   | Moves commits, creates linear history       | Straight line      |

- **Merge** preserves the full branch structure.
- **Rebase** rewrites history for a cleaner look.

---

## Handling Conflicts During Rebase

- If there’s a conflict, Git will pause and let you resolve it.
- After fixing the conflict, run:
  ```bash
  git add <file>
  git rebase --continue
  ```
- If you want to abort the rebase:
  ```bash
  git rebase --abort
  ```

---

## When (Not) to Rebase

- **Do rebase:**  
  - On your own feature branches before merging, to clean up history.
- **Do NOT rebase:**  
  - On public branches that others are using. Rebasing rewrites commit history, which can confuse collaborators.

---

## Visualizing Rebase

Use this command to see your commit history as a graph:

```bash
git log --oneline --graph --all
```

---

> **Tip:**  
> Rebasing is powerful for keeping your history tidy, but always be