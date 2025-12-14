# Dotfiles

My personal development environment configuration

- [Dotfiles](#dotfiles)
  - [Prerequisites](#prerequisites)
  - [Features](#features)
    - [Git configuration](#git-configuration)
    - [PowerShell \& Terminal](#powershell--terminal)
  - [Quick Start](#quick-start)
  - [Credits](#credits)
  - [About Me](#about-me)

## Prerequisites

- **OS**: Windows 11
- **Tools**:
  - PowerShell 7+
  - Git 2.0+
  - Scoop package manager
  - Fonts: Nerd Fonts (FiraCode or JetBrainsMono recommended)
- Optional (for PowerShell features):
  - GnuPG (for Git commit signing)
  - Fzf (fuzzy finder)
  - Oh My Posh (custom prompt)

## Features

- Structure

  ```md
  .
  ├── git/            # Git configuration
  ├── metadata/       # Fonts and additional resources
  ├── powershell      # PowerShell & Terminal setup
  ├── LICENSE
  └── README.md
  ```

### Git configuration

- SSH authentication with GitHub
- GPG commit signing for verified commits
- Custom aliases and configurations

**Setup**: [git/README.md](./git/README.md)

### PowerShell & Terminal

- Core:
  - **PowerShell 7** with custom profile
  - **Windows Terminal** theme and settings
  - **PSReadLine** for intelligent predictions
- Enhancements:
  - **Oh My Posh** - Custom prompt theme
  - **Terminal-Icons** - File/folder icons
  - **fzf** - Fuzzy search (files, history)
  - **z** - Smart directory jumping
  - **Posh-Git** - Git status integration
  - **Custom utilities** - Unix-like commands (touch, which, ll, la, mkcd)

**Setup**: [powershell/README.md](./powershell/README.md)

## Quick Start

1. Clone the repository

    ```powershell
    # Clone this repository
    git clone https://github.com/ngkhang/dotfiles.git
    cd dotfiles
    ```

2. Navigate to specific configuration. Follow the `README.md` in each directory for setup instructions.

## Credits

- [Windows Terminal](https://github.com/microsoft/terminal) - Modern terminal emulator
- [Oh My Posh](https://ohmyposh.dev/) - Prompt theme engine
- [PSReadLine](https://github.com/PowerShell/PSReadLine) - Command line editing
- [fzf](https://github.com/junegunn/fzf)/[PSFzf](https://github.com/kelleyma49/PSFzf) - Fuzzy finder
- [Terminal-Icons](https://github.com/devblackops/Terminal-Icons) - File icons
- [Z](https://www.powershellgallery.com/packages/z) - Directory jumper
- [Posh-Git](https://github.com/dahlbyk/posh-git) - Git integration

## About Me

- [GitHub: @ngkhang](https://github.com/ngkhang/)

Give a ⭐ if this project helped you!
