# Git Configuration

- [Git Configuration](#git-configuration)
  - [Connecting to GitHub with SSH](#connecting-to-github-with-ssh)
    - [Generating a new SSH key](#generating-a-new-ssh-key)
    - [Add a new SSH key](#add-a-new-ssh-key)
  - [Verify Commit Signatures](#verify-commit-signatures)
    - [Generating a new GPG key](#generating-a-new-gpg-key)
    - [Add the GPG key to GitHub account](#add-the-gpg-key-to-github-account)
    - [Telling Git about your signing key](#telling-git-about-your-signing-key)

## Connecting to GitHub with SSH

- Ref: [GitHub: Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

### Generating a new SSH key

1. Generating a new SSH key

    ```bash
    ssh-keygen -t ed25519 -C "your_email@example.com"
    ```

2. Custom key name (Recommendation), default `id_ed25519`

    ```bash
    > Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]
    ```

    - If you custom name key, you need tell SSH to use your new key by adding to `~/.ssh/config`

        ```bash
        Host github.com
            HostName github.com
            User git
            IdentityFile ~/.ssh/YOUR_KEY_FILENAME
        ```

3. Add secure passphrase (Recommendation)

    ```bash
    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]
    ```

4. Adding to ssh-agent

- PowerShell as Admin

    ```bash
    Get-Service -Name ssh-agent | Set-Service -StartupType Manual
    Start-Service ssh-agent
    ```

- PowerShell without elevated permissions

    ```bass
    ssh-add c:/Users/YOU/.ssh/id_ALGORITHM
    ```

### Add a new SSH key

1. Copy the SSH public key to your clipboard `id_ALGORITHM` is your the custom name (default: `id_ed25519`)

    ```bash
    clip < ~/.ssh/id_ALGORITHM.pub
    ```

2. Open GitHub -> Settings -> SSH and GPG keys -> New SHH key or Add SSH key.
3. Custom name for key at `Title` field and paste your public key in `Key` field
4. Testing SSH connection

    ```bash
    # Verify your connection
    ssh -T git@github.com
    Hi USERNAME! You've successfully authenticated...
    ```

## Verify Commit Signatures

### Generating a new GPG key

1. Download and install [the GPG command line tools](https://www.gnupg.org/download/)
2. Generate a GPG key pair

    ```bash
    # GPG version 2.1.17 or greater
    gpg --full-generate-key

    # GPG are not on version 2.1.17 or greater
    gpg --default-new-key-algo rsa4096 --gen-key
    ```

3. Enter prompt questions:

    ```bash
    Please select what kind of key you want:
    (1) RSA and RSA
    (2) DSA and Elgamal
    (3) DSA (sign only)
    (4) RSA (sign only)
    (9) ECC (sign and encrypt) *default*
    (10) ECC (sign only)
    (14) Existing key from card
    Your selection? 9
    Please select which elliptic curve you want:
    (1) Curve 25519 *default*
    (4) NIST P-384
    (6) Brainpool P-256
    Your selection? 1
    Please specify how long the key should be valid.
            0 = key does not expire
        <n>  = key expires in n days
        <n>w = key expires in n weeks
        <n>m = key expires in n months
        <n>y = key expires in n years
    Key is valid for? (0) 0
    Key does not expire at all
    Is this correct? (y/N) y

    GnuPG needs to construct a user ID to identify your key.

    Real name:
    Email address:
    Comment:
    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
    ```

4. Get list the long form of the GPG keys and copy the long form of the GPG key ID you'd like to use (Example: `3AA5C34371567BD2`)

    ```bash
    gpg --list-secret-keys --keyid-format=long

    sec   ed25519/3AA5C34371567BD2 2025-12-12 [SC]
    uid                          Hubot <hubot@example.com>
    ssb   cv25519/4BB6D45482678BE3 2025-12-12 [E]
    ```

5. Paste the text below, substituting in the GPG key ID you'd like to use. Copy your GPG key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----`

    ```bash
    gpg --armor --export 3AA5C34371567BD2
    ```

### Add the GPG key to GitHub account

1. Open GitHub -> **Settings** -> **SSH and GPG keys** -> Next to the "GPG keys" header, click **New GPG key**.
2. In the **Title**, type a name for your GPG key. In the **Key**, paste the GPG key you copied when you [generated your GPG key](#generating-a-new-gpg-key)

### Telling Git about your signing key

1. Open Git Bash. unset `--gpg-sign` configuration to use the default format of `openpgp` if you have previously configured Git to use a different key format

    ```bash
    git config --global --unset gpg.format
    ```

2. Get list the long form of the GPG keys and copy the long form of the GPG key ID you'd like to use (Example: `3AA5C34371567BD2`)

    ```bash
    gpg --list-secret-keys --keyid-format=long

    sec   ed25519/3AA5C34371567BD2 2025-12-12 [SC]
    uid                          Hubot <hubot@example.com>
    ssb   cv25519/4BB6D45482678BE3 2025-12-12 [E]
    ```

3. Set your primary GPG signing key in Git: by the GPG primary key ID (`3AA5C34371567BD2`) or by a subkey (`4BB6D45482678BE3`)

    ```bash
    # Using primary ID
    git config --global user.signingkey 3AA5C34371567BD2

    # Using sub key
    git config --global user.signingkey 4BB6D45482678BE3
    ```

4. Optionally, to configure Git to sign all commits and tags by default, enter the following command:

    ```bash
    git config --global commit.gpgsign true
    git config --global tag.gpgSign true
    ```
