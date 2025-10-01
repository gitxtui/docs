---
title: Working with Remotes
weight: 5
type: "docs"
---

Up until now, we have been working on our local system. Git, however, is built to facilitate collaboration among multiple developers. To let other developers work on our code, we need to publish this code to a website.

---

## Why Not Just Share Files?

You can upload your code anywhere—zip it up and put it on cloud storage like Google Drive or Dropbox, or send the files as an attachment to your friend.  
But these methods **won't preserve your commit history, branches, or collaboration features** (unless you include the hidden `.git` folder, which is risky and not recommended).

**Why use a remote?**
- Keeps your commit history safe and accessible.
- Lets you collaborate with others easily.
- Makes it simple to go back to older versions or branches.
- Saves your work on a server, not just your computer.

---

## What is a Remote?

A **remote** in Git is a link (URL) to a repository hosted somewhere else—like GitHub, GitLab, Bitbucket, or your own server.  
It lets your local repository **sync** (push and pull) with a remote repository, so you can share code and work with others.

**Think of it as:**  
Your local project is your workspace. The remote is a shared folder on the internet where everyone can contribute.

---

## Using a Git Hosting Service

It is much better to use a hosting service that is specially made for Git repositories.  
Popular options include:
- **GitHub** (most popular, especially for open source)
- **GitLab**
- **Bitbucket**
- Self-hosted servers

These platforms offer tools for collaboration, code review, issue tracking, and more.

---

## Connecting a Remote Repository

### Step 1: Create a Remote Repository

Go to [GitHub's new repo page](https://github.com/new) and create a repository.  
- Give it a name.
- Description is optional.
- **Leave all checkboxes under initialization unchecked** (you’ll add files from your computer).

### Step 2: Add the Remote to Your Local Project

In your terminal, inside your project folder, run:

```bash
git remote add origin https://github.com/yourusername/yourrepo.git
```

- `origin` is the **short name** for the remote. It’s a convention for the main remote, but you can use any name.
- Replace the URL with your actual repository link.

**What does this do?**
- Tells Git where to send your code when you push.
- Lets you pull updates from the remote.

---

## Default Remote: `origin`

When you clone a repository, Git automatically sets up a remote called `origin` pointing to the original URL.

```bash
git clone https://github.com/user/repo.git
```

- This creates a local copy and sets `origin` as the default remote.

You can rename it if needed:

```bash
git remote rename origin upstream
```

---

## Managing Remotes

- **List all remotes and their URLs:**
  ```bash
  git remote -v
  ```
- **Add a new remote:**
  ```bash
  git remote add <name> <url>
  ```
- **Remove a remote:**
  ```bash
  git remote remove <name>
  ```
- **Change a remote’s URL:**
  ```bash
  git remote set-url <name> <new-url>
  ```
- You can have multiple remotes (e.g., `origin`, `upstream`).

---

## Remote Branches

Remote-tracking branches show the state of branches on the remote server.

- Examples:
  - `origin/main` → main branch on origin remote.
  - `upstream/dev` → dev branch on upstream remote.

Remote branches are **read-only pointers**. You can’t commit directly to them.

To work on a remote branch:

```bash
git checkout -b feature origin/feature
```

This creates a local branch called `feature` based on the remote branch.

---

## Push & Pull Basics

- **Push (upload changes):**
  ```bash
  git push origin main
  ```
  Sends your local commits to the remote branch.

  ```bash
  git push -u origin feature
  ```
  Pushes and sets up tracking for the `feature` branch.

- **Pull (download + merge):**
  ```bash
  git pull origin main
  ```
  Fetches and merges changes from the remote.

  Equivalent to:
  ```bash
  git fetch origin main
  git merge origin/main
  ```

- **Fetch (download only):**
  ```bash
  git fetch origin
  ```
  Updates info about the remote without merging.

---

## Tracking & Upstream Branches

When you push a branch for the first time:

```bash
git push -u origin feature
```

This sets up a **tracking relationship**.  
Now you can just use:

```bash
git push
git pull
```

without specifying the branch.

Check tracking:

```bash
git branch -vv
```

---

## Cloning vs Forking

- **Clone:**  
  Copies a repository to your machine.
- **Fork:**  
  (GitHub/GitLab feature) Copies a repository under your own account, then you clone it locally.

**Typical open-source flow:**
1. Fork the repo.
2. Clone your fork.
3. Add upstream:
   ```bash
   git remote add upstream https://github.com/original/repo.git
   ```
4. Sync with upstream:
   ```bash
   git fetch upstream
   git merge upstream/main
   ```

---

## Deleting Remote Branches

Delete a branch from the remote:

```bash
git push origin --delete feature
```

The branch still exists locally unless you delete it:

```bash
git branch -d feature
```

---

## Pull vs Fetch vs Rebase

- **git pull:**  
  Fetch + merge remote changes into your branch.
- **git fetch:**  
  Only download changes, don’t merge.
- **git pull --rebase:**  
  Fetch remote changes, then reapply your local commits on top (creates a cleaner history).

---

## Upstream & Multiple Remotes

Common in open-source:

- `origin` → your fork (where you push).
- `upstream` → original repo (where you fetch new changes).

**Example commands:**

```bash
git fetch upstream
git merge upstream/main
```

---

## Remote Tracking Best Practices

- **Always pull before push** to avoid conflicts.
- **Keep branches in sync** with upstream:
  ```bash
  git fetch --all
  ```
- **Delete remote branches after merging** to keep things clean.
- **Don’t force-push** unless absolutely necessary:
  ```bash
  git push -f
  ```

---

## Advanced Remote Operations

- **Mirroring:**
  ```bash
  git clone --mirror <url>
  ```
  Creates a bare clone for full backup.

- **Shallow clone:**
  ```bash
  git clone --depth=1 <url>
  ```
  Only downloads the latest commits (faster, less history).

- **Multiple push URLs:**
  ```bash
  git remote set-url --add origin <url2>
  ```
  Push to multiple remotes at once.

- **Tracking remote renames:**
  ```bash
  git remote rename origin backup
  ```

---

## Authentication & Security

- **HTTPS vs SSH remotes:**
  - HTTPS: Needs username/password or a Personal Access Token (PAT).
  - SSH: Uses SSH keys (`git@github.com:user/repo.git`).

- **PATs (Personal Access Tokens):**
  - Required by GitHub/GitLab instead of passwords for HTTPS.
  - More secure and can be revoked anytime.

---

## Summary Table

| Action                        | Command/Step                                 | Description                                 |
|-------------------------------|----------------------------------------------|---------------------------------------------|
| List remotes                  | `git remote -v`                              | Show all remotes and URLs                   |
| Add remote                    | `git remote add <name> <url>`                | Add a new remote                            |
| Remove remote                 | `git remote remove <name>`                   | Remove a remote                             |
| Set remote URL                | `git remote set-url <name> <new-url>`        | Change remote URL                           |
| List remote branches          | `git branch -r`                              | Show remote-tracking branches               |
| Push changes                  | `git push origin main`                       | Upload commits to remote                    |
| Pull changes                  | `git pull origin main`                       | Download and merge changes                  |
| Fetch changes                 | `git fetch origin`                           | Download changes only                       |
| Delete remote branch          | `git push origin --delete <branch>`          | Remove branch from remote                   |
| Set upstream                  | `git push -u origin <branch>`                | Track remote branch                         |
| Clone repo                    | `git clone <url>`                            | Copy repo to your machine                   |
| Fork repo                     | Use GitHub/GitLab UI                         | Copy repo under your account                |
| Mirror repo                   | `git clone --mirror <url>`                   | Full backup                                 |
| Shallow clone                 | `git clone --depth=1 <url>`                  | Fast, minimal history                       |
| Multiple push URLs            | `git remote set-url --add origin <url2>`     | Push to multiple remotes                    |
| Rename remote                 | `git remote rename origin backup`            | Change remote name                          |

---

> **Tip:**  
> Remotes are the backbone of collaboration in Git.  
> Master remote management to work smoothly with teams and