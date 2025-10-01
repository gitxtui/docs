---
title: Understanding Remote Branches
weight: 10
type: "docs"
---

## What is a Remote Branch?

A **remote branch** is a branch that exists on a remote repository (like GitHub, GitLab, or Bitbucket), not just on your local computer.  
Remote branches let you collaborate with others by sharing your work and keeping your local repository in sync with the remote server.

---

## How Do Remote Branches Work?

- When you **clone** a repository, Git creates local copies of all the remote branches.
- Remote branches are read-only references to the state of branches on the remote server.
- They are named like `origin/main`, `origin/feature/login`, etc.
  - `origin` is the default name for the remote you cloned from.

---

## Common Remote Branch Commands

### 1. Listing Remote Branches

- **List only remote branches:**
  ```bash
  git branch -r
  ```
  Example output:
  ```
  origin/main
  origin/feature/login
  ```

- **List all branches (local and remote):**
  ```bash
  git branch -a
  ```
  Example output:
  ```
  main
  feature/login
  remotes/origin/main
  remotes/origin/feature/login
  ```

---

### 2. Fetching Updates from Remote

- **Update your local copy of remote branches:**
  ```bash
  git fetch
  ```
  - This downloads new commits and branch updates from the remote, but does **not** change your local branches.

---

### 3. Creating a Local Branch from a Remote Branch

If you see a remote branch (like `origin/feature/login`) and want to work on it locally:

```bash
git checkout -b my-local-branch origin/feature/login
```
- This creates a new local branch called `my-local-branch` that starts from the remote branch.

---

### 4. Pushing Local Branches to Remote

- **Push a new local branch to the remote:**
  ```bash
  git push origin <branch-name>
  ```
  - This creates a new branch on the remote server.

---

### 5. Tracking Remote Branches

When you create a local branch from a remote branch, Git can set up **tracking** so your local branch knows which remote branch it’s connected to.

- **Set upstream (tracking) branch:**
  ```bash
  git branch -u origin/main
  ```
  - Now, you can use `git pull` and `git push` without specifying the branch name.

---

## How Do Remote Branches Get Updated?

- When you run `git fetch`, Git updates your local copies of the remote branches.
- When you run `git pull`, Git fetches and then merges changes from the remote branch into your current branch.

---

## Deleting Remote Branches

- **Delete a branch from the remote server:**
  ```bash
  git push origin --delete <branch-name>
  ```
  - This removes the branch from the remote for everyone.

---

## Why Are Remote Branches Important?

- They allow teams to collaborate by sharing code.
- They help keep everyone’s work in sync.
- You can always see what branches exist on the remote and what their latest commits are.

---

> **Tip:**  
> Remote branches are read-only. To make changes, create a local branch from the remote branch, work on it, then push your