# dotfiles

Personal configuration files for developer tools. Targeted at power users — clone and symlink manually.

## Tools

| Tool | Config file | Symlink target |
|------|-------------|----------------|
| ghostty | `ghostty/config` | `~/.config/ghostty/config` |
| shellcheck | `shellcheck/.shellcheckrc` | `~/.shellcheckrc` |

## Usage

Clone the repo:

```bash
git clone https://github.com/<your-username>/dotfiles.git ~/coding_projects/dotfiles
```

Symlink individual configs (example for Ghostty):

```bash
mkdir -p ~/.config/ghostty
ln -sf ~/coding_projects/dotfiles/ghostty/config ~/.config/ghostty/config
```

## Adding a new tool

1. Create a folder named after the tool: `mkdir <tool>`
2. Add config files inside, mirroring their path relative to `~/.config/<tool>/` or `~/`
3. Update the table in this README with the symlink target
