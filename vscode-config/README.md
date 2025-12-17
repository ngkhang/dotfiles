# VSCode configuration

- [VSCode configuration](#vscode-configuration)
  - [Prerequisites](#prerequisites)
  - [Extensions](#extensions)
  - [Features](#features)
  - [Configuration Setup](#configuration-setup)
    - [Settings Configuration](#settings-configuration)
    - [Keybindings Configuration](#keybindings-configuration)
    - [Code Spell Checker Configuration](#code-spell-checker-configuration)
  - [Troubleshooting](#troubleshooting)

## Prerequisites

- Windows 10/11
- [Visual Studio Code](https://code.visualstudio.com/)
- [Nerd Font](https://www.nerdfonts.com/font-downloads) (FiraCode or JetBrainsMono recommended)
- PowerShell 7 (for terminal integration)
- Git installed

## Extensions

- **Git & Version Control**
  - [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - Git supercharged
  - [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) - Visual git history

- **Code Quality & Linting**
  - [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Linter
  - [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Code formatter
  - [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - Inline error highlighting
  - [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - Spell checking
  - [Vietnamese - Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker-vietnamese) - Vietnamese language support

- Language Support
  - [Prisma](https://marketplace.visualstudio.com/items?itemName=Prisma.prisma) - Prisma schema support

- Markdown
  - [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) - Markdown linting
  - [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) - Markdown shortcuts and tools

- Theme and Icons
  - [Everforest](https://marketplace.visualstudio.com/items?itemName=sainnhe.everforest) - Color theme
  - [Catppuccin Icon Theme](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc-icons) - File icons
  - [Fluent Icons](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons) - Product icons

- Utilities
  - [Todo Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree) - Track TODO comments
  - [File Nesting Updater](https://marketplace.visualstudio.com/items?itemName=antfu.file-nesting) - Automatic file nesting config

## Features

- **Appearance**: Everforest theme, color scheme, and UI
- **Editor Settings**: Font, linting, formatting, and inlay hints
- **Terminal Integration** PowerShell 7 as default profile, custom font
- **File Nesting**: Auto-nest related files (configs, tests, styles) based on [antfu's patterns](https://github.com/antfu/vscode-file-nesting-config)
- **Custom Keybindings**
  - **File Management**

   | Keybinding     | Action     |
   | -------------- | ---------- |
   | `Ctrl+N`       | New file   |
   | `Ctrl+Shift+N` | New folder |

  - **Code Folding (Vim-style)**

   | Keybinding        | Action                  |
   | ----------------- | ----------------------- |
   | `Shift+Z R`       | Unfold all              |
   | `Shift+Z M`       | Fold all                |
   | `Shift+Z A`       | Toggle fold             |
   | `Shift+Z O`       | Unfold                  |
   | `Shift+Z C`       | Fold                    |
   | `Shift+Z Shift+C` | Fold recursively        |
   | `Shift+Z J`       | Fold all except current |

## Configuration Setup

### Settings Configuration

1. Open VSCode Settings

   - Press `Ctrl+Shift+P` -> Type `Preferences: Open User Settings (JSON)`
   - Or navigate to `File` -> `Preferences` -> `Settings` -> Click `{}` icon (top right)

2. Copy the provided [`settings.json`](./settings.json) content

### Keybindings Configuration

1. Open Keybindings

   - Press `Ctrl+K Ctrl+S`
   - Or `File` -> `Preferences` -> `Keyboard Shortcuts` -> Click `{}` icon (top right)

2. Copy the provided [`keybindings.json`](./keybindings.json) content

### Code Spell Checker Configuration

1. Create `cspell.json` in your workspace root
2. Copy the provided [`cspell.json`](./cspell.json) content
3. Create `cspell-tool.txt` for custom dictionary
4. Language support: English and Vietnamese

## Troubleshooting
