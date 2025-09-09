---
title: Installation
weight: 2
---

## Installation Script

The easiest way to install `gitx` is by using the installation script. Open your terminal and run the following command:

```bash
curl -sSL https://raw.githubusercontent.com/gitxtui/gitx/master/install.sh | bash
```

This script will automatically detect your operating system and architecture, download the latest release of gitx, and install it to /usr/local/bin.

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
gitx
```



## Where should I go next?

- [Tutorials](/docs/docs/tutorials/): Check out some tutorials for git!