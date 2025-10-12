---
title: "Intro to github actions"
linkTitle: "Github Actions"
date: 2025-10-02
description: "This blog post will guide you through GitHub Actions, developer workflows, CI/CD, and how to set up automated deployment and testing."
author: "garvittsingla" 
---

# The problem
Have you ever thought about how big tech companies manage to push code into production so seamlessly? How do they make sure thousands of test cases run automatically, catch issues before they break things, and still ship updates quickly? It almost feels like magic—code goes in, and polished features come out the other side without chaos.

# The Solution 
The secret isn’t magic at all—it’s automation. In this blog post, we’ll explore how GitHub Actions, developer workflows, and CI/CD pipelines work together to handle testing, automatic deployments, and smooth releases. By the end, you’ll see how these tools make modern software development faster, safer, and much less stressful.

## What is CI/CD

**Continuous Integration (CI)** is the practice of automatically building and testing code every time a team member commits changes to version control. This helps catch bugs early, ensures code quality, and makes collaboration smoother.

**Continuous Delivery (CD)** is a software development approach where code changes are automatically prepared for a release to production. After passing all automated tests, the code is packaged and made ready for deployment, ensuring that new features and fixes can be delivered to users quickly, safely, and with minimal manual intervention.

Together, CI/CD forms a pipeline that automates the process of integrating code, running tests, and delivering applications. This reduces manual work, speeds up releases, and increases confidence in the software you ship.

## Let's explore
[Gitx Docs actions page](https://github.com/gitxtui/docs/actions) , here you can see there are workflows that run on every code commit to master branch
[the GitHub Actions workflow configuration](https://github.com/gitxtui/docs/blob/master/.github/workflows/hugo.yaml), in this file the github spins up a linux instance and runs hugo(SSG generator to generate static files from a readme) and then deploys it to github pages, no need of manual testing of code, no need of manual deplyment of the code, all things got covered by Github itself.

## What happen's exactly
- The workflow file (hugo.yaml) defines a pipeline that triggers automatically on every commit or push to the master branch.

- GitHub provides a Linux virtual environment (runner) where all commands specified in the workflow are executed.

- The workflow installs Hugo, builds the static site from the Markdown/README files, and outputs the final HTML files into the public directory.

- The generated static files are then automatically deployed to the gh-pages branch, which GitHub Pages serves publicly.

## How GitHub Actions Works Behind the Scenes

A GitHub Action workflow is made up of three key components:

- **Events:** Triggers that start your workflow — like `push`, `pull_request`, or a scheduled cron job.
- **Jobs:** Each job runs a series of steps in a virtual environment. Jobs can run in parallel or depend on each other.
- **Runners:** The virtual machines (Linux, macOS, or Windows) where your jobs are executed.

For example, when you push new code to the `main` branch, GitHub detects that event, spins up a Linux runner, installs dependencies, runs your tests, and deploys the result automatically.


## Example: Simple GitHub Actions Workflow

Here’s a basic example of a CI/CD pipeline using Node.js:

```yaml
name: Node CI/CD

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Node
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

```
## What happens exactly

Whenever someone pushes code to the `main` branch, GitHub Actions automatically spins up a **new Ubuntu virtual machine** (called a runner).  
This runner is completely fresh — meaning it doesn’t have any of your project dependencies or tools installed.

Here’s what happens step by step:

1. **Checkout the Code:**  
   The first step uses the `actions/checkout` action to clone your repository into the runner’s environment so that other steps can access your files.

2. **Set up Node.js:**  
   Since the runner is a clean machine, it doesn’t have Node.js installed by default.  
   The `actions/setup-node` action is used to install the required Node.js version defined in your workflow file.

3. **Install Dependencies:**  
   Once Node.js is available, the workflow runs `npm install` (or `yarn install`) to download and set up all the required project dependencies.

4. **Run Tests:**  
   Next, `npm test` executes your automated tests to ensure that your latest changes didn’t break any existing functionality.

5. **Build or Deploy:**  
   If all tests pass successfully, the workflow can then build the project and deploy it automatically — for example, to GitHub Pages, AWS, or another hosting service.

Each time the workflow runs, GitHub creates a **fresh environment**, ensuring your build process is reproducible and isolated from previous runs — a key reason CI/CD pipelines are so reliable.
