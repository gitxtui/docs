---
title: "Contributing to GITx"
linkTitle: "Contribute"

menu: {main: {weight: 30}}
type: "docs"
---

First off, thank you for considering contributing to gitx! It's people like you that make open source such a great community. We welcome any type of contribution, not just code.

## Code of Conduct

This project and everyone participating in it is governed by the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). By participating, you are expected to uphold this code. Please report unacceptable behavior.

## How Can I Contribute?

There are many ways to contribute, from writing tutorials or blog posts, improving the documentation, submitting bug reports and feature requests or writing code which can be incorporated into gitx itself.

### Reporting Bugs

- **Ensure the bug was not already reported** by searching on GitHub under [Issues](https://github.com/gitxtui/gitx/issues).
- If you're unable to find an open issue addressing the problem, [open a new one](https://github.com/gitxtui/gitx/issues/new). Be sure to include a **title and clear description**, as much relevant information as possible, and a **code sample** or an **executable test case** demonstrating the expected behavior that is not occurring.

### Suggesting Enhancements

- Open a new issue to start a discussion about your idea. This is the best way to get feedback before putting in a lot of work.
- Clearly describe the feature, its use case, and why it would be valuable to the project.

### Your First Code Contribution

Unsure where to begin contributing to gitx? You can start by looking through `good first issue` and `help wanted` issues:

- [Good first issues](https://github.com/gitxtui/gitx/labels/good%20first%20issue) - issues which should only require a few lines of code, and a test or two.
- [Help wanted issues](https://github.com/gitxtui/gitx/labels/help%20wanted) - issues which should be a bit more involved than `good first issues`.

### Development Setup

gitx is written in Go. You'll need Go installed on your system (version 1.21 or newer is recommended).

1. Fork the `gitxtui/gitx` repository on GitHub.
2. Clone your fork locally:

    ```sh
    git clone https://github.com/your_username/gitx.git
    cd gitx
    ```

3. Build the project to ensure everything is set up correctly:

    ```sh
    make build
    ```

4. Run the tests:

    ```sh
    make test
    ```

5. Run the project:

    ```sh
    make run
    ```

### Pull Request Process

1. Create a new branch for your feature or bug fix:

    ```sh
    git switch -c feature-your-feature-name
    ```

2. Make your changes and commit them with a descriptive message. We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification. For example:

    ```sh
    git commit -m "feat: Add new panel for commit history"
    ```

3. Push your branch to your fork:

    ```sh
    git push origin feature/your-feature-name
    ```

4. Open a pull request to the `master` branch of the `gitxtui/gitx` repository.
5. Ensure the PR description clearly describes the problem and solution. Include the relevant issue number if applicable.
