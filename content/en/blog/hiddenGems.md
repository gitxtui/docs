---
title: "Git Commands That Will Actually Save Your Day"
linkTitle: "Hidden Git Gems"
date: 2025-10-02
description: "Discover the underrated Git commands that seasoned developers swear by but rarely talk about—powerful tools that solve real problems."
author: "Jatin Goyal"
---

Look, we all know `git commit`, `git push`, and `git pull`. But Git has a treasure trove of commands that can save you hours of frustration—if only you knew they existed. Here are the genuinely useful ones that deserve way more attention.

## `git reflog` — Your Time Machine When Things Go Wrong

Ever executed `git reset --hard` and immediately regretted it? Or accidentally deleted a branch you needed? **This is your safety net.**

```bash
git reflog
```

Reflog shows you *everything* you've done—every commit, reset, checkout, merge. Find the SHA of where you want to be, and:

```bash
git reset --hard HEAD@{2}
```

**Real-world scenario:** You force-pushed to the wrong branch and wiped out work. Reflog lets you recover it. This has saved me more times than I'd like to admit.

## `git add -p` — Stage Like a Pro

Stop staging entire files when you only want some changes. Interactive staging lets you review and stage chunks individually:

```bash
git add -p
```

Git walks you through each change, asking `y/n/s` (yes/no/split). Press `?` for options.

**Why this matters:** You worked on multiple features in one file. This lets you create clean, atomic commits instead of a messy "fixed stuff" commit.

## `git bisect` — Find Bugs Like a Detective

Your code worked last week. Now it doesn't. But there are 50 commits in between. Instead of checking each one manually:

```bash
git bisect start
git bisect bad                 # Current commit is broken
git bisect good <commit-sha>   # This old commit worked
```

Git binary-searches through commits. Mark each one as `good` or `bad`, and it finds the exact commit that introduced the bug.

**Time saved:** Instead of checking 50 commits, you check ~6 (log₂ 50).

## `git stash --include-untracked` — Actually Save Everything

Regular `git stash` only saves tracked files. Add new files? They're ignored. This version saves *everything*:

```bash
git stash -u
# or
git stash --include-untracked
```

**The situation:** You're mid-feature when production breaks. Stash everything (including those new files), fix prod, then pop your stash and continue.

## `git commit --fixup` — Clean History Without the Hassle

You find a typo in a commit from 5 commits ago. Instead of creating "fix typo" commits:

```bash
git commit --fixup <commit-sha>
git rebase -i --autosquash <base-commit>
```

Git automatically marks it as a fixup and merges it into the original commit during interactive rebase.

**Result:** Clean history that doesn't show your mistakes (we all make them, but PRs don't need to know).

## `git worktree` — Multiple Branches, Zero Context Switching

Need to check another branch but don't want to stash or commit your current work?

```bash
git worktree add ../hotfix-branch hotfix
```

This creates a *separate working directory* for that branch. Work on both simultaneously.

**Game changer for:** Reviewing PRs while keeping your current work untouched, or testing a feature while developing another.

## `git log --graph --oneline --all` — Visualize Your History

Understanding branch topology is hard. This makes it crystal clear:

```bash
git log --graph --oneline --all
```

Add an alias to make it permanent:

```bash
git config --global alias.lol "log --graph --oneline --all"
# Now just use: git lol
```

**Pro tip:** Add `--decorate` to see branch and tag names in the visualization.

---

## The Bottom Line

These aren't party tricks—they're practical tools that solve real problems. The difference between a Git novice and someone comfortable with Git isn't knowing *more* commands; it's knowing *which* commands solve which problems.

Bookmark this. Next time you're stuck, one of these will probably save you.

*What's your underrated Git command? Let me know—I'm always looking for new workflow improvements.*
