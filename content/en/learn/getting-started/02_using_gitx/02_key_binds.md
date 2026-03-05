---
title: Keybinds
linkTitle: keybinds
description: Setting custom keybinds in gitx
weight: 2
type: "docs"
---

## Overview

gitx is a keyboard-driven application with customizable keybindings. Every action in gitx can be remapped to your preferred key combination. This guide covers all available keybinds, how to customize them, and best practices for configuring your keyboard shortcuts.

## Configuration

Keybindings are configured in your gitx configuration file located at `~/.config/gitx/config.toml`. The keybindings section uses the following format:

```toml
[keybindings]
action_name = "key_combination"
```

### Key Specification Format

Keys can be specified in several ways:

- **Single keys**: `a`, `1`, `!`, etc.
- **Special keys**: `enter`, `esc`, `tab`, `space`, `up`, `down`, `left`, `right`, `backspace`, `delete`, `home`, `end`, `pgup`, `pgdn`
- **Modifier combinations**: `ctrl+c`, `shift+tab`, `alt+x`
- **Multiple key options**: `q,ctrl+c` (either key will trigger the action)

You can specify multiple alternative keybindings for a single action by separating them with commas.

## Default Keybindings

Here are all the default keybindings organized by category:

### Navigation

| Action | Default Key | Description |
|--------|-------------|-------------|
| `focus_next` | `tab` | Move to the next window |
| `focus_prev` | `shift+tab` | Move to the previous window |
| `focus_main` | `0` | Focus the commit graph (main window) |
| `focus_status` | `1` | Focus the status window |
| `focus_files` | `2` | Focus the files/changes window |
| `focus_branches` | `3` | Focus the branches window |
| `focus_commits` | `4` | Focus the commits window |
| `focus_stash` | `5` | Focus the stash window |
| `focus_command_log` | `6` | Focus the command log window |
| `up` | `k` or `↑` | Move up in lists |
| `down` | `j` or `↓` | Move down in lists |

### Files & Changes

| Action | Default Key | Description |
|--------|-------------|-------------|
| `stage_item` | `a` | Stage the selected file or change |
| `stage_all` | `space` | Stage all changes |
| `discard` | `d` | Discard changes in the selected file |
| `stash` | `s` | Stash the selected file |
| `stash_all` | `S` | Stash all changes |
| `commit` | `c` | Create a new commit |

### Branches

| Action | Default Key | Description |
|--------|-------------|-------------|
| `checkout` | `enter` | Checkout the selected branch |
| `new_branch` | `n` | Create a new branch |
| `delete_branch` | `d` | Delete the selected branch |
| `rename_branch` | `r` | Rename the selected branch |

### Commits

| Action | Default Key | Description |
|--------|-------------|-------------|
| `amend_commit` | `A` | Amend the last commit |
| `revert` | `v` | Revert the selected commit |
| `reset_to_commit` | `R` | Reset to the selected commit |

### Stash

| Action | Default Key | Description |
|--------|-------------|-------------|
| `stash_apply` | `a` | Apply a stash without removing it |
| `stash_pop` | `p` | Apply a stash and remove it |
| `stash_drop` | `d` | Delete the selected stash |

### Miscellaneous

| Action | Default Key | Description |
|--------|-------------|-------------|
| `switch_theme` | `ctrl+t` | Cycle through available themes |
| `toggle_help` | `?` | Show/hide the help panel |
| `escape` | `esc` | Cancel current action |
| `quit` | `q` or `ctrl+c` | Exit gitx |

## Customizing Keybindings

### Basic Customization

To customize a keybinding, add it to the `[keybindings]` section in your `~/.config/gitx/config.toml` file. For example:

```toml
[keybindings]
# Use 'l' instead of 'j' to move down
down = "l"

# Use 'h' instead of 'k' to move up  
up = "h"

# Create a new branch with 'b'
new_branch = "b"
```

### Multiple Key Options

You can specify multiple keys that trigger the same action by separating them with commas:

```toml
[keybindings]
# Stage with either 'a' or 's'
stage_item = "a,s"

# Quit with 'q', ctrl+c, or ctrl+d
quit = "q,ctrl+c,ctrl+d"

# Switch themes with ctrl+t or ctrl+n
switch_theme = "ctrl+t,ctrl+n"
```

### Vim-like Configuration

Many users prefer vim-like keybindings. Here's a complete vim-inspired configuration:

```toml
[keybindings]
# Navigation
up = "k"
down = "j"
left = "h"
right = "l"

# File operations
stage_item = "a"
commit = "c"
discard = "d"
stash = "z"

# Branch operations
new_branch = "b"
checkout = "o"
delete_branch = "x"
rename_branch = "r"

# Commit operations  
amend_commit = "e"
revert = "v"
reset_to_commit = "R"

# General
toggle_help = "?"
quit = "q"
escape = "esc"
```

### Emacs-like Configuration

For those preferring Emacs-style bindings:

```toml
[keybindings]
# Navigation (Ctrl+N/P for next/previous, Ctrl+F/B for forward/backward)
down = "ctrl+n"
up = "ctrl+p"

# Word navigation
focus_next = "ctrl+z"
focus_prev = "ctrl+shift+z"

# Common operations
stage_item = "ctrl+a"
discard = "ctrl+d"
stash = "ctrl+s"
commit = "ctrl+x"

# Help and exit
toggle_help = "ctrl+h"
quit = "ctrl+c"
escape = "esc"
```

### Arrow Key Configuration

If you prefer using arrow keys for navigation:

```toml
[keybindings]
# Use arrow keys
up = "up"
down = "down"
left = "left"
right = "right"

# Keep other keys for actions
stage_item = "a"
commit = "c"
new_branch = "n"
```

## Advanced Examples

### Minimal Keybinding Set

If you only want to change a few keybindings and keep most defaults:

```toml
[keybindings]
# Only customize your most-used actions
commit = "w"
stage_item = "s"
toggle_help = "h"
```

### Dvorak Layout Configuration

For Dvorak keyboard layout users:

```toml
[keybindings]
# Dvorak layout mappings (mapped to QWERTY position)
up = "o"
down = "a"
left = "s"
right = "e"

# Common operations using Dvorak
stage_item = "j"
commit = "b"
discard = "h"
new_branch = "c"
```

### Macros and Complex Workflows

While gitx doesn't support full macro systems, you can use common key combinations for your workflow:

```toml
[keybindings]
# Quick workflow keys
new_branch = "n"
stage_all = "s"
commit = "c"
checkout = "o"
delete_branch = "x"

# Focus shortcuts
focus_files = "2"
focus_branches = "3"
focus_commits = "4"
```

## Tips and Best Practices

1. **Avoid Conflicts**: Don't map the same key combination to multiple actions
2. **Use Modifiers Wisely**: Reserve Ctrl combinations for important actions you use frequently
3. **Consistency**: Try to keep your keybindings consistent with tools you already use (vim, tmux, etc.)
4. **Test Before Committing**: After changing a keybinding, test it in gitx to ensure it works
5. **Document Your Setup**: Keep notes on your custom keybindings for future reference
6. **Preserve Escape**: It's recommended to keep `escape` bound to `esc` as a safe abort key

## Viewing Active Keybindings

When inside gitx, press `?` (or your custom `toggle_help` key) to view the current active keybindings. This will show all keybindings for the currently focused panel.

## Configuration File Location

Your keybindings are stored in: `~/.config/gitx/config.toml`

If this file doesn't exist, gitx will create it with default settings the first time you run the application.
