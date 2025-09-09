---
title: Branch Protection 
weight: 18
---

## What is Branch Protection?

**Branch protection** is a set of rules that prevent unwanted changes to important branches in your repository—like `main`, `master`, or `develop`.  
It’s a safety feature, usually managed on platforms like GitHub, GitLab, or Bitbucket, to keep your codebase stable and secure.

---

## Why Use Branch Protection?

- **Prevent mistakes:**  
  Stops accidental force-pushes, deletions, or direct commits to critical branches.
- **Enforce code review:**  
  Require pull requests and approvals before merging changes.
- **Maintain stability:**  
  Ensure only tested, reviewed code reaches production branches.
- **Automate checks:**  
  Require passing tests, successful builds, or other checks before merging.

---

## Common Branch Protection Rules

### 1. Require Pull Requests

- Disallow direct pushes to protected branches.
- All changes must go through a pull request (PR) for review.

### 2. Require Reviews and Approvals

- Specify that one or more team members must approve a PR before it can be merged.

### 3. Require Status Checks

- Only allow merging if automated tests, builds, or other checks pass.

### 4. Restrict Who Can Push

- Limit who can push, merge, or delete the branch (e.g., only admins or maintainers).

### 5. Prevent Force-Pushes and Deletion

- Block force-pushes (`git push --force`) to avoid rewriting history.
- Prevent accidental or malicious branch deletion.

---

## How to Set Up Branch Protection

### On GitHub

1. Go to your repository on GitHub.
2. Click **Settings** > **Branches**.
3. Add a branch protection rule for your chosen branch (e.g., `main`).
4. Select the rules you want (require PRs, reviews, status checks, etc.).
5. Save the rule.

### On GitLab

1. Go to your repository.
2. Click **Settings** > **Repository** > **Protected Branches**.
3. Choose the branch and set permissions for who can push, merge, or delete.

### On Bitbucket

1. Go to your repository.
2. Click **Repository Settings** > **Branch permissions**.
3. Add rules for your branches.

---

## Example: GitHub Branch Protection

- Require pull request before merging.
- Require at least one approval.
- Require status checks to pass.
- Restrict who can push.
- Block force-pushes and deletion.

---

## When to Protect a Branch

- **Production branches:**  
  Always protect `main`, `master`, or any branch deployed to users.
- **Release branches:**  
  Protect branches used for releases or hotfixes.
- **Develop/integration branches:**  
  Protect if multiple people merge features into them.

---

## Tips for Branch Protection

- **Document your rules:**  
  Make sure everyone on your team knows which branches are protected and why.
- **Review regularly:**  
  Update protection rules as your team or workflow changes.
- **Combine with workflows:**  
  Use protection rules alongside branching workflows for maximum safety.

> **Tip:**  
> Set it up early—don’t wait for a mistake to happen!