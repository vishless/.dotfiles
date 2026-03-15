# README.md

## Repository Overview

This is a modular dotfiles repository for a Linux desktop environment. The three major config components (nvim, polybar, i3) are managed as **Git submodules** — changes to those directories must be committed in their respective upstream repos, then the submodule pointer updated here.

## Submodule Management

```bash
# Initialize/update submodules after cloning
git submodule update --init --recursive

# Update a specific submodule to its latest upstream commit
git submodule update --remote .config/nvim

# After updating a submodule pointer, commit the change in this repo
git add .config/nvim && git commit -m "Update nvim submodule"
```

Submodules and their upstream repos:
- `.config/nvim` → https://github.com/vishless/nvim
- `.config/polybar` → https://github.com/vishless/polybar-config
- `.config/i3` → https://github.com/vishless/i3-config

## Architecture

| Component | Technology | Key config |
|---|---|---|
| Window manager | i3 (Mod4/Super key) | `.config/i3/config` |
| Status bar | Polybar | `.config/polybar/config.ini` |
| Shell | Zsh + Powerlevel10k | `.zshrc`, `.p10k.zsh` |
| Terminal multiplexer | Tmux (prefix: Ctrl+A, vi mode) | `.tmux.conf` |
| Editor | Neovim (Lua, Space leader) | `.config/nvim/init.lua` |

## Polybar

Dual-monitor setup: primary bar on `DP-0`, secondary on `HDMI-0`. The launch script auto-detects monitors via `xrandr`. Custom modules live in `.config/polybar/scripts/` (gmail, network, calendar toggle).

Catppuccin color scheme is used throughout (background `#1e1e2e`, foreground `#cdd6f4`).

## Neovim

Uses native `vim.pack.add()` for plugin management (no third-party plugin manager). Key plugins: `mini.pick` (fuzzy find), `oil.nvim` (file explorer), `vim-fugitive` (git), `claudecode.nvim` (Claude Code integration), catppuccin colorscheme, LSP config.
