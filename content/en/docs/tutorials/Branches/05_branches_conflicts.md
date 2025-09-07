---
title: Handling Merge Conflicts
weight: 8
---

## What is a Merge Conflict?

A **merge conflict** happens when Git cannot automatically combine changes from two branches.  
This usually occurs when two branches have changed the same part of a file, or when one branch deletes a file that the other branch has modified.

---

## Why Do Conflicts Happen?

- Two people (or two branches) edit the **same line** in a file differently.
- One branch deletes a file that the other branch edits.
- Changes are made to the same section of a file in both branches.

Git tries to merge changes automatically, but if it’s unsure which change to keep, it stops and asks you to decide.

---

## How Do You Know There’s a Conflict?

- When you run `git merge` (or `git rebase`), Git will pause and show a message like:
  ```
  Auto-merging file.txt
  CONFLICT (content): Merge conflict in file.txt
  Automatic merge failed; fix conflicts and then commit the result.
  ```
- `git status` will show files with conflicts as **"Unmerged paths"**.

---

## What Does a Conflict Look Like?

Git marks the conflicting area in your file like this:

```text
<<<<<<< HEAD
This is your change from the current branch.
=======
This is the change from the branch you are merging in.
>>>>>>> feature-branch
```

- Everything between `<<<<<<< HEAD` and `=======` is your branch’s version.
- Everything between `=======` and `>>>>>>> branch-name` is the other branch’s version.

---

## How to Resolve a Conflict

1. **Open the conflicted file(s).**
2. **Look for the conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`).
3. **Decide what the final content should be.**
   - Keep your changes, the other branch’s changes, or combine them.
4. **Remove the conflict markers** and edit the file so it looks exactly how you want.
5. **Mark the conflict as resolved** by adding the file:
   ```bash
   git add <filename>
   ```
6. **Complete the merge** by committing:
   ```bash
   git commit
   ```
   - If you were in the middle of a merge, Git may auto-generate a commit message.

---

## Example: Resolving a Conflict

Suppose both branches changed the same line in `hello.txt`:

**After merging, `hello.txt` looks like:**
```text
Hello world!
<<<<<<< HEAD
This is my change.
=======
This is their change.
>>>>>>> feature-branch
Goodbye!
```

**To resolve:**
- Decide which line (or both) you want to keep.
- Edit the file, for example:
  ```text
  Hello world!
  This is my change and their change.
  Goodbye!
  ```
- Save the file.
- Run:
  ```bash
  git add hello.txt
  git commit
  ```

---

## Tips for Avoiding and Handling Conflicts

- **Pull often** to keep your branch up to date.
- **Communicate** with your team about what files you’re working on.
- **Keep commits small and focused** to make conflicts easier to resolve.
- Use tools like VS Code, GitKraken, or SourceTree for visual conflict resolution.

---


> **Tip:**  
> You can always see which files have conflicts with `git status`.  
> Use `git log --merge` to see commits that are causing the