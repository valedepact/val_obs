# Claude Code CLI - Install & Activation

On this machine it's installed as a native standalone binary (not via npm) under
`~/.local/share/claude/versions/`, symlinked at `~/.local/bin/claude`. Same method
works on Arch.

## Install

```bash
curl -fsSL https://claude.ai/install.sh | bash   # download and run the official native installer
```

This installs the binary under `~/.local/share/claude/versions/<version>` and
symlinks it to `~/.local/bin/claude`.

```bash
which claude                              # confirm install location
claude --version                          # confirm it runs
```

## Arch Linux notes

```bash
sudo pacman -Syu                          # update system first
sudo pacman -S curl                       # ensure curl is present (often already is)
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc   # make sure ~/.local/bin is on PATH
source ~/.bashrc
```

## Activation (login)

```bash
claude                                    # launch the CLI
/login                                    # run inside the CLI to start auth
```

This opens a browser-based OAuth flow tied to a Claude.ai or Anthropic Console
account. Once approved, credentials are stored locally at:

```
~/.claude/.credentials.json
```

No `ANTHROPIC_API_KEY` env var is required for this flow - it's only needed if
authenticating via direct API key instead of an account login.

## Generating an SSH Key (for GitHub access)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/id_ed25519_github -N ""
```

- `-t ed25519`  - key algorithm (modern, fast, secure; GitHub's recommended type)
- `-C "..."`    - comment/label embedded in the key, usually your email
- `-f ...`      - file path/name to save the key (avoids overwriting a default key)
- `-N ""`       - empty passphrase, so the key works without prompting each time

This creates two files:
- `~/.ssh/id_ed25519_github`     - private key, stays on this machine, never shared
- `~/.ssh/id_ed25519_github.pub` - public key, paste this into GitHub (Settings -> SSH
  and GPG keys, or a repo's Deploy keys)

```bash
cat ~/.ssh/id_ed25519_github.pub          # view the public key to copy/paste
```

If port 22 is blocked on the network, force SSH over port 443 instead by adding to
`~/.ssh/config`:

```
Host github.com
  HostName ssh.github.com
  Port 443
  User git
  IdentityFile ~/.ssh/id_ed25519_github
  IdentitiesOnly yes
```

```bash
ssh -T git@github.com                     # test the connection once the key is added
```

### Note: this command works for any SSH key, not just GitHub

The same `ssh-keygen` command is used for any service needing SSH key auth
(GitLab, Bitbucket, remote servers/VPS, etc.) - not just GitHub. What can change
depending on the situation:

- `-t ed25519` - fine for almost everything modern; very old servers may only
  support RSA, in which case use `-t rsa -b 4096` instead
- `-f path`    - only needed if you want a separate/named key; without it,
  ssh-keygen uses the default filename and may overwrite an existing default key
- `-N ""`      - empty passphrase, convenient for automation; for a personal key
  you log into manually, use a real passphrase instead for better security
- `-C "..."`   - just a label, never affects function, can be anything or omitted

## Update / reinstall

```bash
claude update                             # update to the latest version, if supported
curl -fsSL https://claude.ai/install.sh | bash   # re-run installer to force latest
```
