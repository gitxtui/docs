---
title: Renaming Branches
weight: 12
type: "docs"
---

## Why Rename a Branch?

Sometimes you create a branch with a quick name, but later want something more descriptive or consistent.  
Renaming branches helps keep your repository organized and clear for everyone working on it.

---

## Renaming a Local Branch

### Rename the Current Branch

If you are **on the branch you want to rename**:

```bash
git branch -m new-branch-name
```
- `-m` stands for "move" (rename).
- This changes the branch name in your local repository.

**Example:**
```bash
git branch -m feature/login feature/authentication
```
Or, if you’re already on `feature/login`:
```bash
git branch -m feature/authentication
```

---

### Rename a Different Local Branch

If you want to rename a branch you’re **not currently on**:

```bash
git branch -m old-branch-name new-branch-name
```

---

## Renaming a Remote Branch

Renaming a branch on the remote (like GitHub) is a two-step process:

### 1. Push the Renamed Branch to Remote

```bash
git push origin new-branch-name
```
- This creates a new branch on the remote with the new name.

### 2. Delete the Old Branch from Remote

```bash
git push origin --delete old-branch-name
```
- This removes the old branch name from the remote.

---

### 3. Reset Upstream Tracking (Optional but Recommended)

If your local branch was tracking the old remote branch, update it to track the new one:

```bash
git branch -u origin/new-branch-name
```

---

## What About Other Collaborators?

- After you rename and push, others will still have the old branch name locally.
- They should fetch the latest changes and delete the old branch locally:
  ```bash
  git fetch origin --prune
  git branch -d old-branch-name
  ```

---

> **Tip:**  
> Renaming branches helps keep your project tidy and your workflow clear—don’t be afraid to update names as your project evolves!
> - Make sure no one else is actively working on the branch you’re renaming, or coordinate with your team.
> - Always double-check branch names before deleting anything on the remote.