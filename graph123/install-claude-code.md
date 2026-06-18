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

## Update / reinstall

```bash
claude update                             # update to the latest version, if supported
curl -fsSL https://claude.ai/install.sh | bash   # re-run installer to force latest
```
