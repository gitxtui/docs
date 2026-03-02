---
title: Installing gitx
weight: 1
type: "docs"
---

## Installation Script

The easiest way to install `gitx` is by using the installation script. Open your terminal and run the following command:

```bash
curl -sSL https://raw.githubusercontent.com/gitxtui/gitx/master/install.sh | bash
```

This script will automatically detect your operating system and architecture, download the latest release of gitx, and install it to `/usr/local/bin`.

## Using go install

Requires `go` to be installed on your system:

```bash
go install github.com/gitxtui/gitx/cmd/gitx@latest
```

This will download the correct binary according to your operating system and place it at `~/go/bin/gitx`.

## Manual Installation

If you prefer to install gitx manually, you can download the latest release from the GitHub Releases page.

Download the appropriate .tar.gz file for your operating system and architecture.
Extract the archive:

```Bash
tar -xzf gitx_*.tar.gz
```

Move the gitx binary to a directory in your $PATH, for example:

```Bash
sudo mv gitx /usr/local/bin/
```

To verify that gitx is installed correctly, change to a directory containing a git repo and run:

```Bash
gitx --version
```

## Next steps:

- [Learn gitx](/docs/learn/getting-started/02_using_gitx): Learn how to use gitx!
- [Tutorials](/docs/learn/tutorials/): Check out some tutorials for git!
