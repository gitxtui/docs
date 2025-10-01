---
title: Squash Commits with Interactive Rebase
weight: 14
type: "docs"
---

## What is Squashing?

**Squashing** means combining multiple commits into a single commit.  
This is useful for cleaning up your commit history before merging a feature branch—so instead of a long list of tiny or "work in progress" commits, you have one clear, meaningful commit.

---

## Why Squash Commits?

- **Cleaner History:**  
  Makes your project history easier to read and understand.
- **Atomic Changes:**  
  Groups related changes together, making it easier to review and revert if needed.
- **Professionalism:**  
  Shows a tidy, intentional history when collaborating or submitting pull requests.

---

## How to Squash Commits Using Interactive Rebase

Suppose your branch has several commits you want to squash into one.

### 1. Start an Interactive Rebase

Decide how many commits you want to squash.  
For example, to squash the last 3 commits:

```bash
git rebase -i HEAD~3
```

### 2. The Rebase Editor

Git will open your default text editor with a list like:

```
pick a1b2c3d First commit
pick b2c3d4e Second commit
pick c3d4e5f Third commit
```

- The commits are listed from oldest (top) to newest (bottom).

### 3. Mark Commits to Squash

- Leave `pick` on the first commit.
- Change `pick` to `squash` (or just `s`) on the commits you want to combine into the first.

Example:

```
pick a1b2c3d First commit
squash b2c3d4e Second commit
squash c3d4e5f Third commit
```

- This will squash the second and third commits into the first.

### 4. Write the Commit Message

- After saving and closing the editor, Git will open another editor window to combine the commit messages.
- Edit the message to describe the combined changes clearly.
- Save and close the editor.

### 5. Finish the Rebase

- If there are no conflicts, you’re done!
- If there are conflicts, Git will pause and ask you to resolve them. After fixing, run:
  ```bash
  git add <file>
  git rebase --continue
  ```

---

## Example: Before and After Squash

**Before:**
```
* c3d4e5f - Third commit
* b2c3d4e - Second commit
* a1b2c3d - First commit
```

**After squashing:**
```
* z9y8x7w - Combined commit (contains all changes)
```

---

## Squash While Merging (Alternative)

You can also squash all commits from a feature branch into one when merging to `main`:

```bash
git checkout main
git merge --squash feature-branch
git commit
```
- This prepares a single combined commit from the feature branch.

---

## When to Squash

- Before merging a feature branch into `main` or `develop`.
- When you want to clean up "work in progress" commits.
- When submitting a pull request and the project prefers a tidy history.

---

> **Tip:**  
> Squashing is a great way to make your project history clean and professional.  
> But remember: **never squash commits on a branch that others are working