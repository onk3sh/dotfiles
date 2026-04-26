# Dotfiles Initial Setup Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create a public GitHub dotfiles repo with a Ghostty terminal config as the first entry.

**Architecture:** Tool-named folders at repo root, each containing config files at their natural relative path. No install automation — users symlink manually. A README documents symlink targets.

**Tech Stack:** Git, GitHub CLI (`gh`), plain text config files.

---

### Task 1: Initialize the git repo

**Files:**
- Create: `.gitignore`

- [ ] **Step 1: Initialize git**

```bash
cd /Users/onkesh/coding_projects/dotfiles
git init
```

Expected output: `Initialized empty Git repository in .../dotfiles/.git/`

- [ ] **Step 2: Create a minimal .gitignore**

Create `.gitignore` with this content:

```
.DS_Store
```

- [ ] **Step 3: Stage and commit**

```bash
git add .gitignore
git commit -m "chore: initialize dotfiles repo"
```

---

### Task 2: Add Ghostty config

**Files:**
- Create: `ghostty/config`

- [ ] **Step 1: Create the ghostty folder and config file**

Create `ghostty/config` with this exact content:

```
# ============================================
# Ghostty Terminal - Complete Configuration
# ============================================

# File: ~/.config/ghostty/config
# Reload: Cmd+Shift+, (macOS)
# View options: ghostty +show-config --default --docs

# --- Typography ---
font-family = JetBrainsMonoNerdFont
font-size = 14
font-thicken = true
adjust-cell-height = 2

# --- Theme and Colors ---
# Catppuccin with automatic light/dark switching
theme = light:Catppuccin Latte,dark:Catppuccin Mocha

# --- Window and Appearance ---
background-opacity = 0.9
background-blur-radius = 20
macos-titlebar-style = transparent
window-padding-x = 10
window-padding-y = 8
window-save-state = always
window-theme = auto

# --- Cursor ---
cursor-style = bar
cursor-style-blink = true
cursor-opacity = 0.8

# --- Mouse ---
mouse-hide-while-typing = true
copy-on-select = clipboard

# --- Quick Terminal (Quake-style dropdown) ---
# Activate with the global keybind configured below
quick-terminal-position = top
quick-terminal-screen = mouse
quick-terminal-autohide = true
quick-terminal-animation-duration = 0.15

# --- Security ---
clipboard-paste-protection = true
clipboard-paste-bracketed-safe = true

# --- Shell Integration ---
shell-integration = detect

# --- Keybindings ---
# Tabs
keybind = cmd+t=new_tab
keybind = cmd+shift+left=previous_tab
keybind = cmd+shift+right=next_tab
keybind = cmd+w=close_surface

# Splits
keybind = cmd+d=new_split:right
keybind = cmd+shift+d=new_split:down
keybind = cmd+alt+left=goto_split:left
keybind = cmd+alt+right=goto_split:right
keybind = cmd+alt+up=goto_split:top
keybind = cmd+alt+down=goto_split:bottom

# Font size
keybind = cmd+plus=increase_font_size:1
keybind = cmd+minus=decrease_font_size:1
keybind = cmd+zero=reset_font_size

# Quick terminal global hotkey
keybind = global:ctrl+grave_accent=toggle_quick_terminal

# Splits management
keybind = cmd+shift+e=equalize_splits
keybind = cmd+shift+f=toggle_split_zoom

# Reload config
keybind = cmd+shift+comma=reload_config

# --- Performance ---
# Generous scrollback (25MB)
scrollback-limit = 25000000
```

- [ ] **Step 2: Stage and commit**

```bash
git add ghostty/config
git commit -m "feat: add Ghostty terminal config (Catppuccin + JetBrains Mono)"
```

---

### Task 3: Add README

**Files:**
- Create: `README.md`

- [ ] **Step 1: Create README.md**

Create `README.md` with this content:

```markdown
# dotfiles

Personal configuration files for developer tools. Targeted at power users — clone and symlink manually.

## Tools

| Tool | Config file | Symlink target |
|------|-------------|----------------|
| ghostty | `ghostty/config` | `~/.config/ghostty/config` |

## Usage

Clone the repo:

\`\`\`bash
git clone https://github.com/<your-username>/dotfiles.git ~/coding_projects/dotfiles
\`\`\`

Symlink individual configs (example for Ghostty):

\`\`\`bash
mkdir -p ~/.config/ghostty
ln -sf ~/coding_projects/dotfiles/ghostty/config ~/.config/ghostty/config
\`\`\`

## Adding a new tool

1. Create a folder named after the tool: `mkdir <tool>`
2. Add config files inside, mirroring their path relative to `~/.config/<tool>/` or `~/`
3. Update the table in this README with the symlink target
```

- [ ] **Step 2: Stage and commit**

```bash
git add README.md
git commit -m "docs: add README with symlink instructions"
```

---

### Task 4: Commit the design spec and push to GitHub

**Files:**
- Already created: `docs/superpowers/specs/2026-04-26-dotfiles-design.md`
- Already created: `docs/superpowers/plans/2026-04-26-dotfiles-initial-setup.md`

- [ ] **Step 1: Stage and commit the docs**

```bash
git add docs/
git commit -m "docs: add design spec and implementation plan"
```

- [ ] **Step 2: Create the public GitHub repo**

```bash
gh repo create dotfiles --public --source=. --remote=origin --push
```

Expected: repo created at `https://github.com/<your-username>/dotfiles` and all commits pushed.

- [ ] **Step 3: Verify**

```bash
gh repo view --web
```

Expected: GitHub opens in browser showing the repo with README rendered.
