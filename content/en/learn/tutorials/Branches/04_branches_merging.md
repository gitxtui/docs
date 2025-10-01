---
title: Merging Branches
weight: 7
type: "docs"
---

## What is Merging?

**Merging** in Git is the process of taking the changes from one branch and combining them into another branch.  
This is how you bring together work from different branches—like adding a new feature you built on a separate branch back into your main project.

---

## Why Merge?

- You might have a `main` branch that holds your stable code.
- You create a `feature` branch to work on something new, so your main code isn’t disturbed.
- When your feature is ready, you want to add it back to `main`—**without losing any work from either branch**.
- Merging lets you combine the work from both branches, keeping all the commit history and changes.

---

## How Does Merging Work?

When you merge, Git tries to automatically combine the changes from both branches.  
If the changes don’t overlap, Git merges them automatically.  
If the same lines were changed in both branches, you’ll get a **merge conflict** (see the Conflicts topic).

---

## Types of Merges in Git

### 1. Fast-Forward Merge

#### What is a Fast-Forward Merge?

A **fast-forward merge** is the simplest type of merge.  
It happens when the branch you’re merging into (like `main`) has not changed since you created your feature branch.  
In this case, Git doesn’t need to do any real "combining"—it just moves the branch pointer forward.

#### Think of it like this:

- Imagine your project is a line of commits.
- You branch off `main` to make a `feature` branch.
- You make some commits on `feature`.
- **Nobody else has made any new commits on `main`** since you branched off.
- When you merge `feature` back into `main`, Git just moves the `main` pointer forward to where `feature` is.

#### Visual Example

Before merge:
```
A---B---C   (main)
         \
          D---E   (feature)
```
Here, `main` is at commit `C`, and `feature` has two extra commits (`D` and `E`).

If `main` hasn’t changed since you branched off, a fast-forward merge just moves `main` forward:

After merge:
```
A---B---C---D---E   (main, feature)
```
Now, both `main` and `feature` point to the same commit (`E`).  
No new "merge commit" is created—Git just advances the pointer.

#### Command

```bash
git checkout main
git merge feature
```

If you see a message like "Fast-forward", you just did a fast-forward merge!

---

### 2. Three-Way Merge

#### What is a Three-Way Merge?

A **three-way merge** happens when both branches have new commits since they split.  
This means both `main` and `feature` have moved forward independently.

#### Why is it called "three-way"?

Because Git looks at three commits:
- The **common ancestor** (where the branches split)
- The **tip of the current branch** (e.g., `main`)
- The **tip of the branch being merged** (e.g., `feature`)

Git compares all three to figure out how to combine the changes.

#### Visual Example

Before merge:
```
A---B---C---F   (main)
         \
          D---E   (feature)
```
- `C` is where you branched off.
- `main` has new commits (`F`).
- `feature` has new commits (`D`, `E`).

When you merge, Git creates a new **merge commit** that combines the changes from both branches:

After merge:
```
A---B---C---F---M   (main)
         \     /
          D---E   (feature)
```
- `M` is the new merge commit.
- Both `main` and `feature` now point to `M`.

#### Command

```bash
git checkout main
git merge feature
```

If you see a message about a "merge commit", you just did a three-way merge!

---

### 3. No-Fast-Forward Merge (`--no-ff`)

#### What is a No-Fast-Forward Merge?

Sometimes, even if a fast-forward merge is possible, you want to **force** Git to create a merge commit.  
This is called a **no-fast-forward merge**.

#### Why would you want this?

- It makes your history clearer.
- You can always see exactly when a feature branch was merged in, even if there were no changes on `main`.

#### Visual Example

Before merge (same as fast-forward):
```
A---B---C   (main)
         \
          D---E   (feature)
```
After a no-fast-forward merge:
```
A---B---C-------M   (main)
         \     /
          D---E   (feature)
```
- `M` is the merge commit, even though it wasn’t strictly needed.

#### Command

```bash
git checkout main
git merge --no-ff feature
```

---

## What Happens During a Merge?

1. **Switch to the branch you want to merge into** (usually `main`):
   ```bash
   git checkout main
   ```
2. **Run the merge command**:
   ```bash
   git merge feature
   ```
3. **Git tries to combine the changes**:
   - If there are no conflicting changes, the merge is automatic.
   - If there are conflicts, Git will pause and ask you to resolve them.

---

> **Tip:**  
> Always make sure you’re on the branch you want to merge **into** before running the merge command!
>
> You can use `git log --graph --oneline` to visualize your branch and merge history.