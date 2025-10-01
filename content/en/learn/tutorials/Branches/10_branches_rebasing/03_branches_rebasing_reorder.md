---
title: Reordering Commits with Interactive Rebase
weight: 15
type: "docs"
---

## Why Reorder Commits?

Sometimes, you make commits in an order that doesn’t make sense for the project’s history.  
Maybe you fixed a typo before adding the main feature, or you want related changes grouped together.  
**Reordering commits** helps you organize your history so it’s logical, readable, and easy to review.

---

## How to Reorder Commits in Git

You use **interactive rebase** to reorder commits.  
This lets you pick up any commit and move it before or after others.

---

### Step-by-Step: Reordering Commits

Suppose your history looks like this (from newest to oldest):

```
* d4e5f6g - Update styles
* c3d4e5f - Add logout button
* b2c3d4e - Fix typo
* a1b2c3d - Add login form
```

But you want "Fix typo" to come after "Add login form" and before "Add logout button".

---

### 1. Start an Interactive Rebase

Decide how many commits you want to reorder (counting backwards from HEAD):

```bash
git rebase -i HEAD~4
```

---

### 2. The Rebase Todo List

Git opens your editor with:

```
pick a1b2c3d Add login form
pick b2c3d4e Fix typo
pick c3d4e5f Add logout button
pick d4e5f6g Update styles
```

- Commits are listed from **oldest (top)** to **newest (bottom)**.
- The order here is the order they will appear in history after the rebase.

---

### 3. Change the Order

To reorder, simply move the lines up or down.

**Example:**  
To put "Fix typo" after "Add logout button":

```
pick a1b2c3d Add login form
pick c3d4e5f Add logout button
pick b2c3d4e Fix typo
pick d4e5f6g Update styles
```

- Save and close the editor.

---

### 4. Finish the Rebase

- Git will replay the commits in the new order.
- If there are conflicts, Git will pause and let you resolve them:
  - Fix the files.
  - Run `git add <file>`.
  - Continue with `git rebase --continue`.

---

## Tips for Reordering Commits

- **Test after reordering:**  
  Changing commit order can sometimes cause conflicts or break your code if commits depend on each other.
- **Keep related changes together:**  
  Grouping related commits makes your history easier to understand.
- **Use meaningful commit messages:**  
  After reordering, you can also use `reword` to update messages for clarity.

---

## When to Reorder Commits

- Before merging a feature branch, to make history logical.
- When you want to group bug fixes or features together.
- When preparing a pull request for review.

---

## Caution

- **Reordering rewrites history.**  
  Only reorder commits on branches that haven’t been pushed/shared, or coordinate with your team.
- Never reorder commits on public/shared branches unless everyone agrees.

---

> **Tip:**  
> Reordering commits is a great way to make your project history logical and professional.  
> Practice on a test branch to get comfortable before using it on important