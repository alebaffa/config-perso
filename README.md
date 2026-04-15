# config-perso

Personal dotfiles managed with [GNU Stow](https://www.gnu.org/software/stow/).

## What's included

| File | Purpose |
|------|---------|
| `.zshrc` | zsh config: oh-my-zsh, antigen, PATH, custom functions |
| `.antigenrc` | Antigen plugin manager config |
| `.gitconfig` | Git settings, delta pager, aliases |
| `.claude/settings.json` | Claude Code: plugins, hooks, model, output style |
| `.claude/statusline*.{sh,txt}` | Claude Code status bar scripts |
| `.claude/plugins/installed_plugins.json` | Claude Code plugin registry |
| `.config/zed/settings.json` | Zed editor global settings |

### Zed project templates (`zed/`)

| File | Purpose |
|------|---------|
| `python-project.zed-settings.json` | Zed project-level settings for Python projects |

Copy into any project's `.zed/settings.json` as needed:

```bash
mkdir -p <project-dir>/.zed
cp zed/python-project.zed-settings.json <project-dir>/.zed/settings.json
```

## Prerequisites

Install these on the new machine first:

```bash
brew install stow git zsh
brew install antigen
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Installation

```bash
git clone <this-repo-url> ~/config-perso
cd ~/config-perso
stow home
```

This creates symlinks in `$HOME` for every file under `home/`.

## Post-install checklist

- [ ] Edit `~/.gitconfig`: replace `your@email.com` with your actual email
- [ ] Edit `~/.gitconfig`: replace `YOUR_SIGNING_KEY` with your GPG/SSH signing key ID
- [ ] Set up AWS profile separately (never stored in this repo)
- [ ] Run `pnpm setup` if you use pnpm (it will configure `PNPM_HOME` automatically)
- [ ] Install Claude Code plugins: open Claude Code and install plugins listed in `.claude/plugins/installed_plugins.json`
- [ ] Set up CCStatusBar app if using the statusline scripts

## Notes

- `installed_plugins.json` records which plugins are installed but paths are machine-specific — plugins need to be reinstalled on the new machine
- `.claude/settings.json` has empty `permissions` — add project-specific permissions per project
