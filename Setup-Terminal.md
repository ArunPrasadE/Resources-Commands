---
tags:
  - command-list
  - linux
  - macos
link: https://computingforgeeks.com/install-zsh-oh-my-zsh-linux/
---
# Zsh Setup — Oh My Zsh, Plugins & Powerlevel10k Theme

Full setup from scratch: install zsh, Oh My Zsh, plugins (zsh-autosuggestions, zsh-syntax-highlighting, sudo, history), and Powerlevel10k theme.

---

## Linux (Debian/Ubuntu)

```bash
# 1. Install dependencies
sudo apt update && sudo apt install -y zsh git curl guake

# 2. Install Oh My Zsh (unattended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# 3. Clone plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting

# 4. Enable plugins (sudo and history are built-in — no clone needed)
sed -i 's/^plugins=(git)/plugins=(git zsh-autosuggestions sudo history zsh-syntax-highlighting)/' ~/.zshrc

# 5. Clone Powerlevel10k theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k

# 6. Set theme
sed -i 's/^ZSH_THEME=.*/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc

# 7. Set zsh as default shell
sudo chsh -s /usr/bin/zsh $USER

# 8. Create terminal log directory
mkdir -p ~/.terminal_logs

# 9. Append auto-script block to ~/.zshrc
cat >> ~/.zshrc << 'EOF'

# Auto-log terminal sessions to ~/.terminal_logs/
if [ -z "$SCRIPT_RUNNING" ]; then
  export SCRIPT_RUNNING=1
  script -q -f ~/.terminal_logs/$(date +%Y-%m-%d_%H-%M-%S)_$$.log
  exit
fi
EOF

# 10. Reload shell (Powerlevel10k wizard launches on first load)
exec zsh

# 11. Install micro - Alternative to vi and nano
sudo apt install micro

# Set color to micro
Open micro -> Ctrl+E -> `set colorscheme cmc-16` -> Ctrl+S -> Ctrl+Q
```

---

## macOS

```bash
# 1. Install dependencies (Homebrew assumed)
brew install zsh git curl

# 2. Install Oh My Zsh (unattended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# 3. Clone plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting

# 4. Enable plugins (sudo and history are built-in — no clone needed)
sed -i '' 's/^plugins=(git)/plugins=(git zsh-autosuggestions sudo history zsh-syntax-highlighting)/' ~/.zshrc

# 5. Clone Powerlevel10k theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k

# 6. Set theme
sed -i '' 's/^ZSH_THEME=.*/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc

# 7. Create terminal log directory
mkdir -p ~/.terminal_logs

# 8. Append auto-script block to ~/.zshrc
cat >> ~/.zshrc << 'EOF'

# Auto-log terminal sessions to ~/.terminal_logs/
if [ -z "$SCRIPT_RUNNING" ]; then
  export SCRIPT_RUNNING=1
  script -q ~/.terminal_logs/$(date +%Y-%m-%d_%H-%M-%S)_$$.log
  exit
fi
EOF

# 9. Reload shell (Powerlevel10k wizard launches on first load)
exec zsh
```

> macOS ships with zsh as the default shell — no `chsh` needed.
> macOS uses BSD sed, which requires `-i ''` (empty string after `-i`). Linux uses GNU sed, which takes `-i` alone.

---

## Verify

```
grep ^ZSH_THEME ~/.zshrc
grep ^plugins= ~/.zshrc
```

Expected:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions sudo history zsh-syntax-highlighting)
```

---

## Plugin Reference

| Plugin | Type | Function |
|---|---|---|
| zsh-autosuggestions | External (cloned) | Fish-style inline suggestions from history |
| zsh-syntax-highlighting | External (cloned) | Real-time command syntax coloring — must be last |
| sudo | Built-in Oh My Zsh | Double-press Esc to prepend `sudo` to current command |
| history | Built-in Oh My Zsh | Adds `h`, `hs`, `hsi` aliases for history search |

---

## Terminal Session Logging

Every new terminal window auto-starts `script`, saving a full session log to `~/.terminal_logs/`.

Log filename format: `YYYY-MM-DD_HH-MM-SS_<PID>.log` — one file per session.

The `SCRIPT_RUNNING` guard prevents infinite recursion: `script` spawns a child shell that would otherwise re-trigger the block.

**Linux** uses `script -q -f` (`-f` flushes output immediately).
**macOS** uses `script -q` (`-f` flag not supported on BSD `script`).

To view a past session:
```
cat ~/.terminal_logs/2026-05-22_10-30-00_12345.log
```

---

## Troubleshooting

### `no such file or directory: /path/to/plugin.zsh` on startup

Stale `source` line in `~/.zshrc`. Remove it — replace the path fragment with the one shown in your error.

**macOS:**
```
sed -i '' '/\/path\/to\/plugin.plugin.zsh/d' ~/.zshrc
```

**Linux:**
```
sed -i '/\/path\/to\/plugin.plugin.zsh/d' ~/.zshrc
```

### `[oh-my-zsh] theme 'powerlevel10k' not found`

Theme clone failed or landed in the wrong path. Verify:
```
ls ~/.oh-my-zsh/custom/themes/powerlevel10k
```

If missing, re-run the clone from step 5.

### `plugins=(...)` line already differs from default

If your `~/.zshrc` has a non-default plugins line, the `sed` in step 4 won't match. Edit `~/.zshrc` manually and add the four plugins inside the existing parentheses. Keep `zsh-syntax-highlighting` last.
