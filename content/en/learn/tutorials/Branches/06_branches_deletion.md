---
title: Deleting Branches
weight: 9
type: "docs"
---

## Why Delete Branches?

Branches are great for working on features, bug fixes, or experiments.  
But once a branch has served its purpose (for example, a feature is merged into `main`), it’s a good idea to delete it.  
This keeps your repository clean and avoids confusion.

---

## Deleting Local Branches

A **local branch** exists only on your computer.

### Delete a Local Branch (Safe)

```bash
git branch -d <branch-name>
```
- Deletes the branch **only if it has been fully merged** into your current branch.
- Prevents you from accidentally deleting work that hasn’t been saved elsewhere.

**Example:**
```bash
git branch -d feature/login
```

### Force Delete a Local Branch

```bash
git branch -D <branch-name>
```
- **Force deletes** the branch, even if it hasn’t been merged.
- Use with caution! You could lose work.

**Example:**
```bash
git branch -D old-experiment
```

---

## Deleting Remote Branches

A **remote branch** is a branch stored on a remote server (like GitHub or GitLab), usually shared with others.

### Delete a Remote Branch

```bash
git push origin --delete <branch-name>
```
- Tells the remote server to remove the branch.
- Other collaborators will no longer see this branch after they fetch or pull.

**Example:**
```bash
git push origin --delete feature/login
```

---

## What Happens After Deletion?

- **Local deletion** only affects your copy of the repository.
- **Remote deletion** removes the branch for everyone, but others may still have a local copy until they delete it themselves.
- Deleting a branch **does not delete the commits**—they remain in the repository history unless they are unreachable from any branch or tag.

---

## Common Scenarios

- **After merging a feature branch:**  
  Delete the feature branch to keep your branch list tidy.
- **Abandoned or stale branches:**  
  Remove branches that are no longer needed to avoid confusion.

---

## Safety Tips

- Always make sure a branch is merged (or you no longer need its changes) before deleting.
- Use `git branch` to list local branches and `git branch -a` to see all branches.
- If you accidentally delete a branch, you can often recover it using `git reflog` (as long as the commits haven’t been garbage collected).

---

> **Tip:**  
> Regularly clean up old branches to keep your repository organized and easy to