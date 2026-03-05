---
title: Custom Themes
linkTitle: custom themes
description: Setting custom themes in gitx
weight: 3
type: "docs"
---

## Overview

gitx comes with built-in themes and supports fully customizable user-defined themes. You can modify colors, styles, and the overall appearance of the interface. This guide covers using built-in themes and creating your own custom themes.

## Built-in Themes

gitx includes the following built-in themes:

- **GitHub Dark** (default) - A clean dark theme based on GitHub's color palette
- **Gruvbox** - A retro groove color scheme

### Using Built-in Themes

To switch between built-in themes:

1. **In gitx**: Press `ctrl+t` (or your custom `switch_theme` key) to cycle through available themes
2. **In config file**: Edit `~/.config/gitx/config.toml` and change the theme:

```toml
theme = "Gruvbox"
```

## Built-in Theme Colors

### GitHub Dark Theme

GitHub Dark is the default theme with GitHub's iconic color scheme:

```
Background: #0d1117
Foreground: #c9d1d9

Normal Colors:
  Black:    #24292E    | Bright Black:    #6e7681
  Red:      #ff7b72    | Bright Red:      #ffa198
  Green:    #3fb950    | Bright Green:    #56d364
  Yellow:   #d29922    | Bright Yellow:   #e3b341
  Blue:     #58a6ff    | Bright Blue:     #79c0ff
  Magenta:  #bc8cff    | Bright Magenta:  #d2a8ff
  Cyan:     #39c5cf    | Bright Cyan:     #56d4dd
  White:    #b1bac4    | Bright White:    #f0f6fc

Dark Colors (for selected items):
  Dark Black:    #1b1f23
  Dark Red:      #d73a49
  Dark Green:    #28a745
  Dark Yellow:   #dbab09
  Dark Blue:     #2188ff
  Dark Magenta:  #a041f5
  Dark Cyan:     #12aab5
  Dark White:    #8b949e
```

### Gruvbox Theme

Gruvbox is a warm, retro-inspired color scheme:

```
Background: #282828
Foreground: #ebdbb2

Normal Colors:
  Black:    #282828    | Bright Black:    #928374
  Red:      #cc241d    | Bright Red:      #fb4934
  Green:    #98971a    | Bright Green:    #b8bb26
  Yellow:   #d79921    | Bright Yellow:   #fabd2f
  Blue:     #458588    | Bright Blue:     #83a598
  Magenta:  #b16286    | Bright Magenta:  #d3869b
  Cyan:     #689d6a    | Bright Cyan:     #8ec07c
  White:    #a89984    | Bright White:    #ebdbb2

Dark Colors (for selected items):
  Dark Black:    #1d2021
  Dark Red:      #9d0006
  Dark Green:    #79740e
  Dark Yellow:   #b57614
  Dark Blue:     #076678
  Dark Magenta:  #8f3f71
  Dark Cyan:     #427b58
  Dark White:    #928374
```

## Creating Custom Themes

Custom themes are stored as TOML files in `~/.config/gitx/themes/`. Each custom theme file defines a color palette that gitx uses to render the interface.

### Theme File Location

Create your custom theme files in: `~/.config/gitx/themes/`

The directory will be created automatically when gitx first runs. If it doesn't exist, create it manually:

```bash
mkdir -p ~/.config/gitx/themes
```

### Theme File Format

Each theme is a TOML file with the following structure:

```toml
# Global foreground and background colors
fg = "#e8e8e8"
bg = "#1a1a1a"

# Standard colors (8 colors)
[normal]
Black = "#2d2d2d"
Red = "#f2777a"
Green = "#99cc99"
Yellow = "#ffcc99"
Blue = "#6699cc"
Magenta = "#cc99cc"
Cyan = "#99cccc"
White = "#e8e8e8"

# Light/bright colors (8 colors)
[bright]
Black = "#999999"
Red = "#ff9999"
Green = "#99ff99"
Yellow = "#ffff99"
Blue = "#99ccff"
Magenta = "#ff99ff"
Cyan = "#99ffff"
White = "#ffffff"

# Dark colors for selected items
[dark]
Black = "#000000"
Red = "#cc0000"
Green = "#00cc00"
Yellow = "#cccc00"
Blue = "#0000cc"
Magenta = "#cc00cc"
Cyan = "#00cccc"
White = "#999999"
```

### Color Format

Colors must be specified in **hexadecimal format** with a `#` prefix, e.g., `#ff7b72`. You can use any 6-digit hex color code.

### Creating Your First Custom Theme

Here's an example of creating a minimalist theme:

1. Create the file `~/.config/gitx/themes/minimal.toml`:

```toml
# Minimal Light Theme
fg = "#000000"
bg = "#ffffff"

[normal]
Black = "#000000"
Red = "#990000"
Green = "#009900"
Yellow = "#999900"
Blue = "#000099"
Magenta = "#990099"
Cyan = "#009999"
White = "#cccccc"

[bright]
Black = "#666666"
Red = "#ff0000"
Green = "#00ff00"
Yellow = "#ffff00"
Blue = "#0000ff"
Magenta = "#ff00ff"
Cyan = "#00ffff"
White = "#ffffff"

[dark]
Black = "#333333"
Red = "#660000"
Green = "#006600"
Yellow = "#666600"
Blue = "#000066"
Magenta = "#660066"
Cyan = "#006666"
White = "#999999"
```

2. In gitx, change your theme in `~/.config/gitx/config.toml`:

```toml
theme = "minimal"
```

Note: The theme name is the filename without the `.toml` extension.

## Theme Examples

### Dracula Theme

A popular dark theme with vibrant colors:

```toml
fg = "#f8f8f2"
bg = "#282a36"

[normal]
Black = "#21222c"
Red = "#ff5555"
Green = "#50fa7b"
Yellow = "#f1fa8c"
Blue = "#69b7f0"
Magenta = "#ff79c6"
Cyan = "#8be9fd"
White = "#f8f8f2"

[bright]
Black = "#6272a4"
Red = "#ff6e6e"
Green = "#69ff94"
Yellow = "#ffffa5"
Blue = "#d6acff"
Magenta = "#ff92df"
Cyan = "#a4ffff"
White = "#ffffff"

[dark]
Black = "#000000"
Red = "#cc0000"
Green = "#00cc00"
Yellow = "#cccc00"
Blue = "#0000cc"
Magenta = "#cc00cc"
Cyan = "#00cccc"
White = "#666666"
```

### Solarized Dark

A precision colors theme for machines and people:

```toml
fg = "#839496"
bg = "#002b36"

[normal]
Black = "#073642"
Red = "#dc322f"
Green = "#859900"
Yellow = "#b58900"
Blue = "#268bd2"
Magenta = "#d33682"
Cyan = "#2aa198"
White = "#eee8d5"

[bright]
Black = "#586e75"
Red = "#cb4b16"
Green = "#93a1a1"
Yellow = "#839496"
Blue = "#657b83"
Magenta = "#6c71c4"
Cyan = "#63b132"
White = "#fdf6e3"

[dark]
Black = "#000000"
Red = "#990000"
Green = "#009900"
Yellow = "#999900"
Blue = "#000099"
Magenta = "#990099"
Cyan = "#009999"
White = "#666666"
```

### Nord Theme

An arctic, north-bluish color palette:

```toml
fg = "#eceff4"
bg = "#2e3440"

[normal]
Black = "#3b4252"
Red = "#bf616a"
Green = "#a3be8c"
Yellow = "#ebcb8b"
Blue = "#81a1c1"
Magenta = "#b48ead"
Cyan = "#88c0d0"
White = "#eceff4"

[bright]
Black = "#4c566a"
Red = "#d08770"
Green = "#c3e88d"
Yellow = "#ffeb3b"
Blue = "#8fbcbb"
Magenta = "#c9a87c"
Cyan = "#8fbcbb"
White = "#ffffff"

[dark]
Black = "#0d0e11"
Red = "#7a1515"
Green = "#1d5e1d"
Yellow = "#5d5d00"
Blue = "#0d0d4d"
Magenta = "#4d004d"
Cyan = "#004d4d"
White = "#4d4d4d"
```

### One Dark

Atom's popular One Dark theme:

```toml
fg = "#abb2bf"
bg = "#282c34"

[normal]
Black = "#1e2127"
Red = "#e06c75"
Green = "#98c379"
Yellow = "#d19a66"
Blue = "#61afef"
Magenta = "#c678dd"
Cyan = "#56b6c2"
White = "#abb2bf"

[bright]
Black = "#5c6370"
Red = "#e06c75"
Green = "#98c379"
Yellow = "#d19a66"
Blue = "#61afef"
Magenta = "#c678dd"
Cyan = "#56b6c2"
White = "#c8ccd4"

[dark]
Black = "#000000"
Red = "#990000"
Green = "#009900"
Yellow = "#999900"
Blue = "#000099"
Magenta = "#990099"
Cyan = "#009999"
White = "#666666"
```

## Using Custom Themes

Once you've created a custom theme file, you can use it by:

1. **Via config file**: Edit `~/.config/gitx/config.toml` and set:
   ```toml
   theme = "your_theme_name"
   ```
   (Use the filename without `.toml` extension)

2. **Via keybinding**: Use `ctrl+t` (or your custom `switch_theme` key) to cycle through all available themes, including your custom ones.

## Color Reference for UI Elements

While gitx automatically generates the complete UI styling from your color palette, here's what each color group is used for:

- **Normal Colors**: Used for regular text, UI elements, and general content
- **Bright Colors**: Used for highlights, emphasis, and important elements
- **Dark Colors**: Used for selected items, active focus states, and backgrounds
- **Foreground (fg)**: Default text color
- **Background (bg)**: Default background color

## Tips for Creating Themes

1. **Test Your Palette**: Create high-contrast between foreground and background for readability
2. **Use Consistent Hues**: Keep related colors in the same hue family for visual consistency
3. **Consider Accessibility**: Ensure sufficient contrast ratios for people with color vision deficiency
4. **Name Meaningfully**: Use descriptive names for your theme files (e.g., `monokai_dark.toml` instead of `theme1.toml`)
5. **Validate Colors**: Use online tools to check color contrast and hex validity
6. **Test in gitx**: Launch gitx after creating a theme to see how it looks in practice

## Color Tools

These tools can help you create and validate custom themes:

- [Colorhexa](https://www.colorhexa.com/) - Hex color lookup and conversion
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) - Check color contrast ratios
- [Coolors](https://coolors.co/) - Color palette generator
- [Vibrancy](https://www.vibrancy.app/) - iOS color palette generator

## Troubleshooting

**Theme not appearing in the theme switcher:**
- Ensure the file is in `~/.config/gitx/themes/` directory
- Verify the filename ends with `.toml`
- Check that all color values are valid hex codes

**Colors look wrong:**
- Verify all color values use the `#` prefix (e.g., `#ff0000`)
- Ensure hex codes are 6 digits long
- Check that the TOML syntax is valid

**gitx crashes when loading theme:**
- Use a simple theme with the example above as a template
- Verify no duplicate color entries exist
- Check that there are no special characters in color values

## Configuration File Location

Your theme configuration is determined by the `theme` setting in: `~/.config/gitx/config.toml`

Your custom theme files are stored in: `~/.config/gitx/themes/`
