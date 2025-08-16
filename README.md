# Dev Configs

This repo contains my personal development configs for various tools and languages.

## Zsh

### Custom Prompt

<img width="146" height="21" alt="image" src="https://github.com/user-attachments/assets/417531dc-999b-43d4-8e1a-4528ba29c178" />

#### `.zshrc-custom-prompt`

A clean, informative prompt that shows exactly what you need to know at a glance:

**What you'll see:**

- 🕐 Current time (because who doesn't lose track of time while coding?)
- 🌐 `user@host` only when SSH'd into remote machines
- 📁 Current directory (smartly abbreviated to the tip of the directory tree)
- 🌿 Git branch/status with a handy `*` for dirty repos
- 🐍 Active Python virtual environment
- ❯ A friendly green caret to keep things crisp

**Under the hood:** Uses helper functions for Git and venv detection, hooks into Zsh's `precmd` for dynamic updates, and only shows SSH info when you actually need it.

### Custom Welcome

<img width="313" height="168" alt="image" src="https://github.com/user-attachments/assets/2f2b6afe-8aba-4f58-aa5a-408266d868ec" />

#### `.zshrc-custom-welcome`

Why settle for a boring terminal when you can have a personalized greeting? This welcome banner brings some life and helpful information to your shell:

**The experience:**

- 👋 Personalized greeting that adapts to time of day
- 🎨 ASCII art that changes based on morning/afternoon/evening
- 📅 Today's date
- 🔧 Quick environment snapshot showing your Node.js and Python versions
- 🚫 Smart enough to only show once per session (no spam!)

**The magic:** Dynamically detects time of day, formats dates properly with ordinal suffixes, and guards against duplicate displays. It's the little terminal welcome you didn't know you needed.

### Installation

You can enable the Zsh welcome banner and prompt in either of the following ways:

#### Option 1: Copy & paste into your `.zshrc` (prompt last)

- Open `~/.zshrc`.
- Paste the contents of `zsh/.zshrc-custom-welcome` first.
- Paste the contents of `zsh/.zshrc-custom-prompt` after it (this must come last so it can set `PROMPT`).

Example layout:

```zsh
# ...existing code...

# --- Welcome banner ---
# (paste contents of zsh/.zshrc-custom-welcome here)

# --- Prompt (must come last) ---
# (paste contents of zsh/.zshrc-custom-prompt here)
```

#### Option 2: Clone locally and import from your `.zshrc`

1. Clone the repo (or use your existing local path):

```bash
git clone https://github.com/michaellennon-wdfw/dev-configs ~/.config/dev-configs
```

2. Source the files in `~/.zshrc` (prompt last):

```zsh
# ...existing code...

# Dev configs
if [[ -r ~/.config/dev-configs/zsh/.zshrc-custom-welcome ]]; then
  source ~/.config/dev-configs/zsh/.zshrc-custom-welcome
fi

# Prompt (must come last as it sets PROMPT)
if [[ -r ~/.config/dev-configs/zsh/.zshrc-custom-prompt ]]; then
  source ~/.config/dev-configs/zsh/.zshrc-custom-prompt
fi
```
