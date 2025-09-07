---
title: Branching Workflows
weight: 17
---

## What is a Branching Workflow?

A **branching workflow** is a strategy for how you and your team use branches to organize work in a Git repository.  
It defines how features, fixes, releases, and collaboration happen—making teamwork smoother and your project history clearer.

---

## Why Use a Workflow?

- **Organization:**  
  Keeps features, fixes, and releases separate.
- **Collaboration:**  
  Allows multiple people to work independently.
- **Safety:**  
  Protects stable code from unfinished or experimental changes.
- **Traceability:**  
  Makes it easy to see what was done, when, and by whom.

---

## Common Branching Workflows

### 1. Feature Branch Workflow

- **Each new feature or fix gets its own branch.**
- Branches are created from the main branch (often called `main` or `master`).
- When finished, the feature branch is merged back into `main`.

**Example:**
```bash
git checkout -b feature/login
```
- Work on your feature, then merge:
```bash
git checkout main
git merge feature/login
```

**Benefits:**  
Keeps features isolated, makes code review easier.

---

### 2. Gitflow Workflow

A popular workflow for larger projects.

- **Main branches:**
  - `main` (or `master`): Always stable, production-ready code.
  - `develop`: Integration branch for new features.
- **Supporting branches:**
  - `feature/*`: For new features.
  - `release/*`: For preparing releases.
  - `hotfix/*`: For urgent fixes to production.

**Example:**
```bash
git checkout -b feature/payment develop
```
- Merge features into `develop`, then create a release branch when ready.

**Benefits:**  
Organized, clear process for releases and hotfixes.

---

### 3. Trunk-Based Development

- **Everyone works on a single branch** (usually `main`).
- Feature branches are short-lived—merged quickly.
- Encourages frequent integration and small changes.

**Example:**
```bash
git checkout -b quick-fix
# Make changes
git checkout main
git merge quick-fix
```

**Benefits:**  
Fast-paced, reduces merge conflicts, ideal for continuous integration.

---

### 4. Fork + Pull Request Workflow

Common on platforms like GitHub and GitLab.

- **Each contributor forks the repository** (creates their own copy).
- Work happens in branches on the fork.
- Changes are proposed back to the original repo via a **pull request** (PR).

**Example:**
- Fork the repo.
- Create a branch on your fork:
  ```bash
  git checkout -b feature/docs
  ```
- Push and open a PR to the main repo.

**Benefits:**  
Safe for open source, allows code review before merging.

---

## Choosing a Workflow

- **Small teams/projects:**  
  Feature branch or trunk-based is often enough.
- **Large teams/multiple releases:**  
  Gitflow or fork + PR workflows add structure.
- **Open source:**  
  Fork + PR is standard.

---

## Workflow Tips

- **Name branches clearly:**  
  Use descriptive names like `feature/login`, `bugfix/header`, or `hotfix/payment-crash`.
- **Keep branches focused:**  
  One feature or fix per branch.
- **Merge often:**  
  Avoid long-lived branches to reduce conflicts.
- **Protect important branches:**  
  Use branch protection rules on `main` or `develop` to prevent accidental changes.

---

> **Tip:**  
> Pick a workflow that matches your team size, release process, and collaboration style.  
> Document your workflow so everyone knows how to