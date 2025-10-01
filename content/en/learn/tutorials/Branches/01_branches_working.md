---
title: Working with Branches
weight: 4
type: "docs"
---

## Listing Branches

To see your **local branches**, use:

```bash
git branch
```

> **Expected output:**  
> ```
> * main
> ```
<br><br>

To list **all branches** (including remote branches), use:

```bash
git branch -a
```

> **Expected output:**  
> ```
> * main
>   remotes/origin/main
> ```
<br><br>

To list **Remote branches** (including remote branches), use:

```bash
git branch -r
```

> **Expected output:**  
> ```
> * remotes/origin/main
> ```
<br>

---

- The branch marked with an asterisk (`*`) is your **currently active branch**.
- Any changes or commits you make are added to this branch.

---

> **Tip:**  
> Use branches to keep your work organized and your main branch stable!