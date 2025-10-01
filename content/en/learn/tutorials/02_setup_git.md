---
title: Getting started with GIT
weight: 2
type: "docs"
---

## 1. Installation

You only need to install Git once.

- **Windows**: Download from [GIT](https://git-scm.com) and install.
    
- **Mac**:
    
    ```bash
    brew install git
    ```
    
- **Linux (Ubuntu/Debian)**:
    
    ```bash
    sudo apt update && sudo apt install git
    ```

    - **ArchLinux**
    ```bash
    sudo pacman -Syu && sudo pacman -S git
    ```
    

Check if it’s installed:

```bash
git --version
```

---

## 2. The Git Workflow (The Big Picture)

Before typing anything, let’s understand **how Git thinks**.

Every project has:

1. **Working Directory** → where you edit files.
    
2. **Staging Area** → a "waiting room" where you prepare files you want to save.
    
3. **Repository (Repo)** → Git’s database where snapshots (commits) are stored.
    

The basic cycle is:

**Edit files → Stage them → Commit them**

If you keep this 3-step cycle in mind, Git will never feel scary.

---

## 3. Getting Started – Your First Project

### Step 1: Tell Git who you are (only once)

git config --global user.name "Your Name" 
git config --global user.email "your@email.com"

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

This info will be attached to your changes.

### Step 2: Create a Git repository

A repository = your project folder + Git’s history tracking.


```bash
mkdir myproject
cd myproject
git init
```

 You just told Git: _“Hey, start tracking this folder.”_    
 [**Caution**: *DO NOT* initialize git in your local file system (like home, desktop, etc), always create a new file and then initialize git.]

### Step 3: Add a file


```bash
echo "Hello Git" > hello.txt
```

### Step 4: Check status


```bash
git status
```

It will say: _“Untracked file: hello.txt”_ → meaning Git sees it but hasn’t saved it yet.

### Step 5: Stage the file


```bash
git add hello.txt
```

Now hello.txt is in the **staging area**.

### Step 6: Commit the file


```bash
git commit -m "First commit: added hello.txt"
```

 Congratulations You just made your first snapshot!

---

## 4. Understanding Key Git Concepts

### 🔹 Commits = Snapshots

Every commit is like _saving a checkpoint in a video game_. If something breaks, you can go back.

### 🔹 Branches = Alternate Timelines

Imagine you want to try a new feature but don’t want to break your main project.  
You create a **branch**:


```bash
git branch new-feature
git switch new-feature
```

Now you’re working in a separate timeline. When ready, you merge it back into main.

### 🔹 Logs = History Book

See your commits:


```bash
git log --oneline
```

It’s like flipping through a project’s diary.

### 🔹 Remote Repositories = Cloud Backup

Your local repo is only on your computer. A remote (like GitHub) is a **backup + collaboration space**.

- Add a remote:
    
    ```bash
    git remote add origin https://github.com/user/repo.git
    ```
    
- Upload your work:
    
    ```bash
    git push origin main
    ```
    
- Download updates from others:
    
    ```bash
    git pull
    ```
    

---

## 5. Correct Workflow to Follow (as a beginner)

Here’s a **safe and simple workflow** you should practice until it becomes second nature:

1. **Start a project**:
    ```bash
    git init # or
    git clone <url>
    ```
    
2. **Make changes** → edit files normally
    
3. **Check status**:
    ```bash
    git status
    ```
    
4. **Stage changes**:
    ```bash
    git add <file>
    ```
    
5. **Commit changes**:
    ```bash
    git commit -m "message"
    ```
    
6. **Repeat steps 2–5 often**
    
7. **When working with others**:
    
    - Pull updates first:
        ```bash
        git pull
        ```
    - Make your changes
    - Push them:
        ```bash
        git push
        ```
        

 Think of it as: **Pull → Work → Add → Commit → Push**

---

## 6. Common Real-Life Examples

- **Accidentally deleted a file?**
    

    ```bash
    git checkout -- file.txt
    ```
    
- **Want to see what you changed before committing?**
    

    ```bash
    git diff
    ```
    
- **Oops, wrong commit message?**
    

    ```bash
    git commit --amend
    ```
    
- **Need to undo last commit (but keep files)?**
    

    ```bash
    git reset --soft HEAD~1
    ```
    

---

## 7. Limitations

- Large files (like videos, datasets) → use Git LFS.
    
- Merging conflicts can happen → but they’re just Git saying: _“I don’t know which version to keep; please decide.”_
    
- Git feels confusing at first → but with practice, it becomes second nature.
    

---

## 8. FAQ
**Q: Is Git the same as GitHub?**  
No. Git is the tool. GitHub is a website to host Git projects.

**Q: Do I need to know all commands?**  
No. Start with `init`, `status`, `add`, `commit`, `log`, `push`, `pull`. That’s enough for 80% of real-world use.

**Q: Can I break my project using Git?**  
Not really. Since Git keeps history, you can always roll back.

---

## 9. Next Steps

Now that you know the basics:

- Practice by creating small projects.
    
- Use branches for experiments.
    
- Try pushing to GitHub and collaborating.
    

Over time, you’ll naturally pick up advanced features like rebasing, stashing, and cherry-picking.

---
