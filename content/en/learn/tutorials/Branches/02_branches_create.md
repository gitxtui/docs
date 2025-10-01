---
title: Creating Branches
weight: 5
type: "docs"
---


## Creating a Branch   

#### Command 1: Create only
```bash
git branch <branch-name>
```
- Creates a new branch.
- Does not switch to it.
- You’re still on the same branch as before.

#### Command 2: Create + switch
```bash
git checkout -b <branch-name>
```

- Shortcut: creates the branch and switches to it.
- Older syntax.

#### Command 3: Modern way
```bash
git switch -c <branch-name>
```

- Recommended modern syntax.
- Does the same thing as checkout -b.