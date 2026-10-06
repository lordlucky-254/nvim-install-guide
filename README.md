# Neovim Install & Launch Guide

A quick, copy-paste guide to installing [Neovim](https://neovim.io) and launching it — including from **VS Code**.

> Tested with **Neovim 0.12.5** on Linux (x86_64). Works on any Linux distro; macOS and Windows notes included.

---

## 1. Install Neovim

### Option A — Official tarball (Linux, no sudo required)

This installs into your home directory — no root password needed:

```bash
mkdir -p ~/.local/opt ~/.local/bin
curl -fsSL -o /tmp/nvim.tar.gz \
  https://github.com/neovim/neovim/releases/download/stable/nvim-linux-x86_64.tar.gz
tar -xzf /tmp/nvim.tar.gz -C ~/.local/opt
ln -sf ~/.local/opt/nvim-linux-x86_64/bin/nvim ~/.local/bin/nvim
```

Make sure `~/.local/bin` is on your `PATH` (add to `~/.bashrc` or `~/.zshrc` if needed):

```bash
export PATH="$HOME/.local/bin:$PATH"
```

### Option B — Package managers

| Distro/OS   | Command                          |
| ----------- | -------------------------------- |
| Debian/Ubuntu | `sudo apt install neovim`      |
| Fedora      | `sudo dnf install neovim`        |
| Arch        | `sudo pacman -S neovim`          |
| macOS       | `brew install neovim`            |
| Windows     | `winget install Neovim.Neovim`   |

### Option C — From source

Requires CMake, `ninja`, and a C compiler:

```bash
git clone https://github.com/neovim/neovim.git
cd neovim
make CMAKE_BUILD_TYPE=Release
sudo make install
```

---

## 2. Verify the install

```bash
nvim --version
```

You should see something like:

```
NVIM v0.12.5
Build type: Release
```

---

## 3. Launch Neovim

```bash
nvim                  # empty buffer
nvim file.txt         # open (or create) a file
nvim .                # open the current directory (file explorer)
nvim +10 file.txt     # open a file at line 10
```

Inside Neovim, type `:q` + Enter to quit, `:help` for help.

---

## 4. Launch Neovim from VS Code

Neovim runs fine in VS Code's integrated terminal:

1. Open VS Code (`code .` from a folder, or use the GUI).
2. Open the integrated terminal:
   - **Linux/Windows:** `` Ctrl+` ``
   - **macOS:** `` Ctrl+` `` or **Terminal → New Terminal**
3. Run:

   ```bash
   nvim .
   ```

Tips:

- Run `code -r .` inside that nvim's `:!` shell (or another terminal) to reopen the folder in the VS Code window.
- Prefer VS Code's own editor with Neovim keybindings? Install the **"Neovim" extension** (`vscode-neovim`) — it drives VS Code with your nvim config instead of opening a TUI.
- To always start VS Code from a terminal, install the shell command: **Ctrl+Shift+P → "Shell Command: Install 'code' command in PATH"**.

---

## 5. First-run sanity check

Once inside Neovim:

| Keys        | Action                                  |
| ----------- | --------------------------------------- |
| `:e file`   | Edit a file                             |
| `:w`        | Save                                    |
| `:q`        | Quit                                    |
| `:q!`       | Quit without saving                     |
| `<Esc>`     | Back to normal mode (from Insert mode)  |
| `:help tutor` | Built-in 30-minute tutorial            |

---

## Troubleshooting

- **`nvim: command not found`** — `~/.local/bin` is not on your `PATH`; re-check step 1.
- **Old version from apt** — distro repos lag behind; use the official tarball (Option A) for the latest release.
- **Terminal can't render it** — use a truecolor terminal (e.g. kitty, alacritty, WezTerm, or VS Code's built-in terminal).
