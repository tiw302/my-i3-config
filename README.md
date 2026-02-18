![WM](https://img.shields.io/badge/WM-i3-orange)
![Lines](https://img.shields.io/badge/lines-143-blue)
![Bloat](https://img.shields.io/badge/bloat-0%25-brightgreen)
![Style](https://img.shields.io/badge/style-minimal-ff69b4)

# my-i3-config

**clean, minimal, and fast. every line serves a purpose.**

this config is the result of actually reading the i3 documentation and understanding what each setting does. no copy-paste from random reddit threads, no outdated commented code from 2018.

143 lines total. everything is documented and easy to customize. designed for speed and simplicity.

## Preview ( •̀ ˘ •́)ノð

![Full Setup](assets/Preview_1.png)
![Full Setup](assets/Preview_2.png)
![Status bar](assets/Status_bar.png)
![Workspaces](assets/Workspaces.png)

## What You Get

**Window Manager:**
- Vanilla i3wm (stable and well-maintained)
- Vim keybindings (j/k/l/;) plus arrow keys for flexibility
- Fast workspace switching
- Intuitive resize mode

**Status Bar:**
- Custom [cbar](https://github.com/tiw302/cbar) - 1.9MB, written in pure C
- Alternative i3status configuration included

**Keybindings:**
- Logical and easy to remember
- `$mod` = Super/Windows key (Alt is reserved for terminal applications)
- Covers all essential functions

**Appearance:**
- Dark theme for reduced eye strain
- Minimal borders for clear focus indication
- Clean color scheme

## Keybindings Reference

`$mod` = Super/Windows key. Here's everything you need to know:

| Shortcut | Action | Notes |
| :--- | :--- | :--- |
| `$mod + Enter` | Terminal (`kitty`) | Fast, GPU-accelerated |
| `$mod + d` | App Launcher (`rofi`) | Clean dmenu theme |
| `$mod + F2` | Browser (`qutebrowser`) | Keyboard-driven |
| `$mod + F3` | File Manager (`thunar`) | Also `$mod+Shift+p` |
| `Print` | Screenshot (`flameshot`) | Select and copy |
| `$mod + Shift + q` | Close window | Graceful close |
| `$mod + f` | Toggle fullscreen | Maximize window |
| `$mod + Shift + space` | Toggle floating | For dialogs |
| `$mod + space` | Toggle focus mode | Float ↔ tile |
| `$mod + r` | Resize mode | Use j/k/l/; or arrows |
| `$mod + Shift + r` | Restart i3 | Apply config changes |
| `$mod + Shift + e` | Exit i3 | With confirmation |
| `$mod + [1-9,0]` | Switch workspace | Quick access |
| `$mod + Shift + [1-9,0]` | Move window | To workspace |
| `$mod + h` | Split horizontal | Logical splits |
| `$mod + v` | Split vertical | |
| `$mod + s/w/e` | Layout modes | Stack/tab/split |

**Navigation:**
- `$mod + j/k/l/;` = Vim-style (left/down/up/right)
- `$mod + arrows` = Alternative arrow key navigation
- `$mod + Shift + [same]` = Move windows instead of focus

**Media Keys:**
- Volume and brightness controls work automatically on most laptops

## Important Note

This repository contains **only** the i3 config file.

**Not included:**
- kitty configuration (terminal)
- rofi themes (launcher)
- picom settings (compositor)
- wallpaper
- GTK/Qt themes

These need to be configured separately. The screenshots show my personal setup, but you'll need to customize these components yourself.

## Requirements

Please install these packages before using this config:

**Core Applications:**
- `i3-wm` - The window manager itself
- `kitty` - Terminal emulator
- `rofi` - Application launcher
- `qutebrowser` - Web browser
- `thunar` - File manager

**Utilities:**
- `picom` - Compositor for smooth rendering
- `flameshot` - Screenshot tool
- `brightnessctl` - Brightness control (for laptops)
- `dex` - Autostart handler for .desktop files
- `nm-applet` - Network manager system tray
- `blueman` - Bluetooth manager (optional)

**Status Bar:**
- [cbar](https://github.com/tiw302/cbar) - Custom status bar
- OR `i3status` - Standard i3 status bar

**Fonts (Important):**
- `IBM Plex Mono` - Main interface font (size 11)
- `IBM Plex Sans Thai` - Thai text support (size 11)

Without these fonts, text rendering will not look correct.

## Installation Guide

### Step 1: Install Dependencies

**Arch Linux:**
```bash
sudo pacman -S i3-wm kitty rofi qutebrowser thunar picom flameshot \
               brightnessctl dex network-manager-applet blueman \
               ttf-ibm-plex
```

**Debian/Ubuntu:**
```bash
sudo apt install i3 kitty rofi qutebrowser thunar picom flameshot \
                 brightnessctl dex network-manager-gnome blueman \
                 fonts-ibm-plex
```

**Fedora:**
```bash
sudo dnf install i3 kitty rofi qutebrowser thunar picom flameshot \
                 brightnessctl dex network-manager-applet blueman \
                 ibm-plex-fonts-all
```

### Step 2: Setup Status Bar

**Option A: Using cbar (recommended)**
```bash
git clone https://github.com/tiw302/cbar.git ~/cbar
cd ~/cbar
make
sudo make install
```

**Option B: Using i3status**
- Edit lines 129-130 in the config file
- Comment out: `status_command ~/cbar`
- Uncomment: `status_command i3status`

### Step 3: Install Configuration

```bash
# Backup your existing config (recommended)
cp ~/.config/i3/config ~/.config/i3/config.backup

# Clone this repository
git clone https://github.com/tiw302/my-i3-config
cd my-i3-config

# Copy the config file
cp config ~/.config/i3/config

# Reload i3
i3-msg restart
```

### Step 4: First Login

1. Log out of your current session
2. Select "i3" from your display manager
3. Log in
4. Press `$mod+Shift+r` to reload the configuration

## Customization

All customization can be done by editing the config file:

### Changing Applications

Modify lines 14-19 to use your preferred applications:
```bash
bindsym $mod+Return exec kitty              # Change terminal
bindsym $mod+F2 exec qutebrowser            # Change browser
```

### Adjusting Colors

- **Window borders:** Lines 122-125
- **Status bar:** Lines 132-141

Use hex color codes (e.g., `#ffffff` for white).

### Switching to i3status

If you prefer the standard i3status bar, edit lines 129-130:
```bash
# Comment this line:
# status_command ~/cbar

# Uncomment this line:
status_command i3status
```

Then press `$mod+Shift+r` to reload.

## Configuration Structure

Here's what each section does:

```
Lines 1-4:    Basic settings (mod key, font, window dragging)
Lines 6-10:   Autostart applications
Lines 12-28:  Keybindings (applications and media controls)
Lines 30-62:  Window management (focus, movement, layouts)
Lines 64-67:  System commands (reload, restart, exit)
Lines 69-103: Workspace configuration
Lines 105-120: Resize mode settings
Lines 122-126: Window color scheme
Lines 127-142: Status bar configuration
```

Total: **143 lines** of clear, documented configuration.

## Performance

This setup is designed to be lightweight and fast:

**Resource Usage:**
- i3wm: ~10-15 MB RAM
- cbar: ~2 MB RAM  
- kitty: ~20-30 MB RAM
- Total: ~35-50 MB for the entire desktop environment

**Comparison with other desktop environments:**
- GNOME: 800+ MB
- KDE Plasma: 500+ MB
- XFCE: 200+ MB

**Startup Time:**
- Config parsing: <10 ms
- Autostart apps: ~500 ms (hardware dependent)
- First render: Nearly instant

## Troubleshooting

### i3 Won't Start

Check the i3 log for errors:
```bash
cat ~/.i3/i3log
```

Common issues:
- Missing dependencies
- Syntax error in config file

### Rofi Doesn't Launch

Test manually:
```bash
rofi -show drun -theme dmenu
```

If it fails, try reinstalling rofi.

### Status Bar Shows Error

If using cbar but haven't installed it:
1. Follow the cbar installation steps above, or
2. Switch to i3status (see customization section)

### Fonts Look Incorrect

Verify fonts are installed:
```bash
fc-list | grep "IBM Plex"
```

If nothing appears, reinstall the fonts and log out/in.

### Brightness Keys Don't Work

Add yourself to the video group:
```bash
sudo usermod -aG video $USER
```

Then log out and log back in.

### Network Applet Missing

Make sure network-manager-applet is installed:
```bash
# Arch
sudo pacman -S network-manager-applet

# Debian/Ubuntu  
sudo apt install network-manager-gnome
```

### Bluetooth Applet Missing

Uncomment line 8 in the config:
```bash
exec --no-startup-id blueman-applet
```

Then reload with `$mod+Shift+r`.

## Design Philosophy

This configuration follows these principles:

**Simplicity:**
- Every line has a clear purpose
- No unnecessary complexity
- Easy to understand and modify

**Performance:**
- Minimal resource usage
- Fast startup and operation
- No animations or visual effects that slow things down

**Usability:**
- Logical keybindings
- Support for both vim keys and arrows
- Clear visual feedback

**Maintainability:**
- Well-documented
- No outdated or commented-out code
- Easy to extend

## Extending This Config

Want to add more features? Here are some suggestions:

### Adding Notifications

```bash
# Install dunst
sudo pacman -S dunst

# Add to config after line 10:
exec --no-startup-id dunst
```

### Adding Wallpaper

```bash
# Install feh
sudo pacman -S feh

# Add to config after line 10:
exec --no-startup-id feh --bg-scale ~/Pictures/wallpaper.jpg
```

### Compositor Effects

Picom configuration is separate from i3. Edit `~/.config/picom/picom.conf` for blur, shadows, and transparency effects.

## Why This Configuration?

**What's Different:**
- Clean and minimal (143 lines total)
- No commented-out experimental code
- All keybindings are documented
- Both vim and arrow key navigation
- Optimized for speed
- Easy to customize

**What's Not Included:**
- Window gaps (personal preference - you can add them if you like)
- Complex application-specific window rules
- Experimental features
- Unused keybindings

This keeps the config simple and focused on what matters most: a fast, efficient window manager.

## Contributing

Contributions are welcome! If you have:
- Bug fixes
- Documentation improvements
- Better keybinding suggestions
- Performance optimizations

Please open an issue first to discuss changes before submitting a pull request.

## Alternative Configurations

If this config doesn't fit your needs, here are some alternatives:

**Want window gaps?** Try Sway or i3-gaps configurations
**Want animations?** Consider Hyprland
**Want more features?** Check out larger i3 configs on GitHub
**Want GUI configuration?** Consider desktop environments like XFCE

Everyone has different preferences, and that's perfectly fine!

## Technical Details

### Why Vim Keys for Navigation?

- Home row position requires less hand movement
- Consistent with other keyboard-driven tools (vim, tmux, qutebrowser)
- Arrow keys are still available as an alternative

### Why Super Key Instead of Alt?

- Alt is used by many terminal applications
- Super key is rarely used by other programs
- Reduces keybinding conflicts

### Configuration Size

143 lines is enough to cover:
- All essential keybindings
- Window management
- Workspace configuration
- Visual customization
- Autostart applications

Additional features can be added as needed without bloating the base configuration.

## Credits

**Created by:** [@tiw302](https://github.com/tiw302)

**Uses:**
- [i3wm](https://i3wm.org/) - Tiling window manager
- [cbar](https://github.com/tiw302/cbar) - Custom status bar

**Thanks to:**
- The i3 development team
- Everyone who has starred this repository
- Contributors and testers

## Support

**If you find this helpful:**
- ⭐ Star the repository
- Share it with others
- Provide feedback
- Contribute improvements

**If you need help:**
- Check the troubleshooting section above
- Review the i3 documentation
- Open an issue with detailed information
- Provide error messages and logs

**When opening issues, please include:**
- Your Linux distribution
- i3 version (`i3 --version`)
- Error messages from `~/.i3/i3log`
- Steps to reproduce the problem

## License

MIT License - Feel free to use, modify, and distribute this configuration.

Attribution is appreciated but not required.

---

**Last Updated:** 2026-02-15

**Status:** Actively maintained

**Configuration Size:** 143 lines

**Philosophy:** Simple, fast, and functionalq
