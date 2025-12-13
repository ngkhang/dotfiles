# Git Configuration Guide

- [Git Configuration Guide](#git-configuration-guide)
  - [Git Configuration](#git-configuration)
  - [SSH Authentication](#ssh-authentication)
    - [Generate SSH key](#generate-ssh-key)
    - [Add Key to GitHub](#add-key-to-github)
  - [GPG Commit Signing](#gpg-commit-signing)
    - [Generate GPG Key](#generate-gpg-key)
    - [Add GPG Key to GitHub](#add-gpg-key-to-github)
  - [Troubleshooting](#troubleshooting)
    - [SSH connection fails](#ssh-connection-fails)
    - [GPG signing fails](#gpg-signing-fails)

## Git Configuration

- Basic setup as username, mail, etc.
- Useful aliases
- See my [.gitconfig](./.gitconfig)

## SSH Authentication

- Ref: [GitHub: Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

### Generate SSH key

1. **Generating a new SSH key**

   - **Recommended settings**:
     - Custom key name (e.g., `id_ed25519_github`)
     - Secure passphrase

        ```bash
        ssh-keygen -t ed25519 -C "your_email@example.com"
        ```

   - **Custom Key Configuration**: If using a custom key name, create `~/.ssh/config`

        ```bash
        Host github.com
            HostName github.com
            User git
            IdentityFile ~/.ssh/YOUR_KEY_NAME
        ```

2. **Configure SSH Agent (Windows)**

    ```powershell
    # Run as Administrator
    Get-Service ssh-agent | Set-Service -StartupType Manual
    Start-Service ssh-agent

    # Add key (normal user)
    ssh-add ~/.ssh/YOUR_KEY_NAME
    ```

### Add Key to GitHub

1. **Copy SSH public key**

    ```bash
    clip < ~/.ssh/YOUR_KEY_NAME.pub
    ```

2. GitHub → `Settings` → `SSH and GPG keys` → `New SSH key`
3. **Test connection**

    ```bash
    # Verify your connection
    ssh -T git@github.com
    Hi USERNAME! You've successfully authenticated...
    ```

## GPG Commit Signing

- **Prerequisites**: Install [GnuPG tool](https://www.gnupg.org/download/)

### Generate GPG Key

1. **Generate a GPG key pair**

   - Recommended options:
     - Key type: `(9) ECC (sign and encrypt)`
     - Curve: `(1) Curve 25519`
     - Expiration: `0` (no expiration)

    ```bash
    # GPG version 2.1.17 or greater
    gpg --full-generate-key

    # GPG are not on version 2.1.17 or greater
    gpg --default-new-key-algo rsa4096 --gen-key
    ```

2. **Export GPG Public key and copy it**:

    ```bash
    # List keys
    gpg --list-secret-keys --keyid-format=long

    # Example output:
    sec   ed25519/3AA5C34371567BD2 2025-12-12 [SC]
    uid                          Your Name <email@example.com>
    ssb   cv25519/4BB6D45482678BE3 2025-12-12 [E]

    # Export key (use the ID after ed25519/)
    gpg --armor --export 3AA5C34371567BD2
    ```

3. Copy the output from `-----BEGIN PGP PUBLIC KEY BLOCK-----` to `-----END PGP PUBLIC KEY BLOCK-----`

### Add GPG Key to GitHub

1. GitHub → `Settings` → `SSH and GPG keys` → `New GPG key`
2. **Configure Git Signing**

    ```bash
    # If you previously used a different GPG format, reset it first
    git config --global --unset gpg.format

    # Set signing key (use your GPG key ID)
    git config --global user.signingkey 3AA5C34371567BD2

    # Optional: Auto-sign all commits and tags
    git config --global commit.gpgsign true
    git config --global tag.gpgsign true
    ```

## Troubleshooting

### SSH connection fails

- Verify key is added to ssh-agent: `ssh-add -l`
- Check GitHub key permissions

### GPG signing fails

- Ensure GPG key ID is correct: `gpg --list-secret-keys --keyid-format=long`
- Verify key is added to GitHub
