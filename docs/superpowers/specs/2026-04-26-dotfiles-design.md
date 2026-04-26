# Dotfiles Repo Design

**Date:** 2026-04-26

## Goal

A public GitHub repository to version-control personal tool configurations (dotfiles), starting with Ghostty terminal. Targeted at power users who manage their own symlinks.

## Scope

- Version-control config files for multiple tools over time
- Start with Ghostty terminal configuration
- No install automation — users symlink manually

## Repo Structure

```
dotfiles/
├── README.md          # symlink targets documented per tool
├── ghostty/
│   └── config         # symlink target: ~/.config/ghostty/config
└── (future: zsh/, git/, tmux/, etc.)
```

Each tool gets a top-level folder named after the tool. Only customized config files are included — no full directory trees. As new tools are added, a new folder is created and the README is updated with the symlink target.

## Ghostty Config

Base config sourced from https://gist.github.com/davila7/5b07f55a6e65a06c121da9702d10c2e2

Key settings:
- Font: JetBrains Mono Nerd Font, size 14
- Theme: Catppuccin Latte (light) / Catppuccin Mocha (dark), auto-switching
- Background opacity 0.9 with blur
- Quake-style quick terminal via `ctrl+grave_accent`
- Tab and split keybindings
- 25MB scrollback

## README

Documents the symlink target for each tool:

| Tool | Config file in repo | Symlink target |
|------|--------------------|--------------------|
| ghostty | `ghostty/config` | `~/.config/ghostty/config` |

## Non-Goals

- Install scripts or automation
- Secrets or API keys (repo is public)
- Machine-specific templating
