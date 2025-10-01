---
title: Interactive Rebase in Git
weight: 13
type: "docs"
---

## What is Interactive Rebase?

**Interactive rebase** is a powerful Git feature that lets you rewrite, edit, reorder, squash, or even delete commits in your branch’s history.  
It’s called "interactive" because Git opens an editor and lets you choose exactly what happens to each commit.

---

## Why Use Interactive Rebase?

- **Clean up messy commit history** before sharing your work.
- **Combine (squash) multiple commits** into one.
- **Edit commit messages** for clarity or consistency.
- **Reorder commits** to make history logical.
- **Remove unwanted commits** (like mistakes or debug code).
- **Split a commit** into smaller, more focused commits.

---

## How to Start an Interactive Rebase

Decide how many commits you want to work with (counting backwards from your current commit):

```bash
git rebase -i HEAD~n
```
- Replace `n` with the number of commits you want to edit.
- Example: To edit the last 4 commits:
  ```bash
  git rebase -i HEAD~4
  ```

---

## The Rebase Todo List

Git opens your default text editor with a list like:

```
pick a1b2c3d Add login form
pick b2c3d4e Fix typo
pick c3d4e5f Add logout button
pick d4e5f6g Update styles
```

- Each line is a commit, from oldest (top) to newest (bottom).
- The word `pick` means "keep this commit as is."

---

## What Can You Do in Interactive Rebase?

Replace `pick` with one of these commands:

- **pick**: Use the commit as is.
- **reword**: Edit the commit message.
- **edit**: Pause to change the commit’s content (amend).
- **squash**: Combine this commit into the previous one (good for cleanup).
- **fixup**: Like squash, but discard this commit’s message.
- **drop**: Remove the commit entirely.
- **exec**: Run a shell command.

**Example: Squash and Reword**
```
pick a1b2c3d Add login form
squash b2c3d4e Fix typo
reword c3d4e5f Add logout button
pick d4e5f6g Update styles
```

---

## Step-by-Step Example: Squashing and Editing

Suppose you want to:

- Combine "Fix typo" into "Add login form"
- Edit the message for "Add logout button"

1. Start the rebase:
   ```bash
   git rebase -i HEAD~4
   ```
2. In the editor, change:
   ```
   pick a1b2c3d Add login form
   squash b2c3d4e Fix typo
   reword c3d4e5f Add logout button
   pick d4e5f6g Update styles
   ```
3. Save and close the editor.
4. Git will prompt you to combine commit messages for the squashed commits.
5. Git will prompt you to edit the commit message for the "reword" commit.
6. If there are conflicts, Git will pause and ask you to resolve them:
   - Fix the files.
   - Run `git add <file>`.
   - Continue with `git rebase --continue`.

---

## Aborting or Continuing

- **Abort the rebase and return to original state:**
  ```bash
  git rebase --abort
  ```
- **Continue after resolving conflicts:**
  ```bash
  git rebase --continue
  ```

---

## When to Use Interactive Rebase

- Before merging a feature branch, to tidy up your commits.
- When you want to split, combine, or reorder commits for clarity.
- When you need to edit a commit message or remove a mistake.

---

## Caution

- **Interactive rebase rewrites history.**  
  Only use it on branches that haven’t been pushed/shared with others, or coordinate with your team.
- Never rebase public/shared branches unless everyone agrees.

---

> **Tip:**  
> Interactive rebase is one of the most powerful tools in Git for crafting a clean, professional commit history.  
> Practice on a test branch to get comfortable before using it on important