# VectorFlux — Cyberpunk Retro Space GTK Theme

A sharp-edged, compact fork of Libadwaita with a cyberpunk space aesthetic. Less rounded, more utilitarian, warm instrument panel colors. Inspired by 70s/80s sci-fi interfaces — think *Alien*, *Blade Runner*, *Star Trek*.

## Design Philosophy

- **Sharp geometry** — Border radius reduced from Libadwaita's default 15px to just 2–3px
- **Compact layout** — Tighter spacing, padding, and margins throughout; less wasted space
- **Flat surfaces** — Minimal shadows, clean lines, utilitarian dashboard feel
- **Warm accent palette** — Orange-gold primary colors evoking retro instrument panel lights

## Version Support

| Version | Directory | Target Apps |
|---------|-----------|-------------|
| GTK4 + Libadwaita | `gtk/4.0/` | Modern GNOME apps (Settings, Nautilus, Firefox) |
| GTK3 | `gtk-3.0/` | Most current desktop apps (Steam, VSCode, Discord) |
| GTK2 | `gtk-2.0/` | Legacy applications fallback |

## Installation

### GTK4 + Libadwaita (Recommended)

```bash
# Copy theme files to your local themes directory
mkdir -p ~/.themes/VectorFlux/gtk/4.0
cp gtk/4.0/*.css ~/.themes/VectorFlux/gtk/4.0/

# Activate via gsettings or GNOME Tweaks
gsettings set org.gnome.desktop.interface gtk-theme 'VectorFlux'
```

**Test immediately:**
```bash
GTK_THEME=VectorFlux gnome-control-center
```

### GTK3

```bash
# Copy to local themes directory
mkdir -p ~/.themes/VectorFlux/gtk-3.0
cp gtk-3.0/*.css ~/.themes/VectorFlux/gtk-3.0/

# Activate
gsettings set org.gnome.desktop.interface gtk-theme 'VectorFlux-gtk3'
```

**Test immediately:**
```bash
GTK_THEME=VectorFlux-gtk3 firefox
```

### GTK2 (Legacy)

```bash
# Copy to local themes directory
mkdir -p ~/.themes/VectorFlux/gtk-2.0
cp gtk-2.0/gtkrc ~/.themes/VectorFlux/gtk-2.0/

# Activate for a session
export GTK2_RC_FILES="$HOME/.themes/VectorFlux/gtk-2.0/gtkrc"
```

## File Structure

```
VectorFlux/
├── gtk/                    # GTK4 + Libadwaita
│   └── 4.0/
│       ├── gtk.css         # Main entry point + retro space styling
│       ├── light.css       # Light theme color variables
│       └── dark.css        # Dark mode (media query)
├── gtk-3.0/               # GTK3
│   ├── gtk.css            # Light mode main stylesheet
│   └── gtk-dark.css       # Dark mode overrides
├── gtk-2.0/               # GTK2 (legacy fallback)
│   └── gtkrc              # Complete light/dark theme definitions
├── docs/
│   ├── README.md          # You are here
│   └── palette.json       # Quick-reference color swatches
└── assets/                # Optional: custom icons, logos
    └── icons/             # (empty — uses system icons)
        └── schemes/       # (reserved for future use)
```

## Color Palette

| Role | Light Value | Dark Value |
|------|-------------|------------|
| Window BG | `#f3f0ea` (warm off-white) | `#15151a` (deep space black) |
| View BG | `#ffffff` | `#1c1b20` |
| Header Bar | `#ebe7df` | `#1e1d23` |
| **Accent Primary** | `#e8590c` (warm orange) | `#e8590c` |

### Full Palette

```
blue-3:   #4a90d9    teal-3:   #2ba8b5
green-3:  #3da868    yellow-3: #e8b82d
orange-3: #e8590c*   red-3:    #dc4c3f
pink-3:   #d46aa0    purple-3: #9752b6

(* = primary accent, instrument panel orange)
```

## Customization Guide

### Changing the Accent Color

Edit these files and change the orange-gold accent:

**GTK4:** `gtk/4.0/light.css` — Change `--accent-orange` and `--accent-bg-color`
**GTK3:** `gtk-3.0/gtk.css` — Change `@define-color accent_bg_color`
**GTK2:** `gtk-2.0/gtkrc` — Change the primary button color variable

### Making It Even More Compact

Reduce padding in the main stylesheet:

```css
/* GTK4 example */
row, actionrow { min-height: 22px; }
button { min-height: 20px; padding: 2px 8px; }
entry { padding: 2px 6px; }
```

### Adjusting Border Radius

Change `--window-radius` in `light.css` or modify all hardcoded values across the theme.

For a fully square look, set border radius to `0px` everywhere.

## Comparison: Libadwaita vs VectorFlux

| Feature | Libadwaita (default) | **VectorFlux** |
|---------|---------------------|-----------------|
| Border radius | 15px (heavily rounded) | **2–3px (sharp)** |
| Button padding | Default (bushy) | **Compact (6px + 10px)** |
| Scrollbars | Thick, rounded | **Thin (6px), sharp** |
| Shadows | Prominent depth | **Flat, minimal** |
| Accent color | Blue `#3584e4` | **Orange `#e8590c`** |

## Credits

Original design inspired by [Libadwaita](https://gitlab.gnome.org/GNOME/libadwaita) by the GNOME team.

Adapted with a cyberpunk space aesthetic inspired by 1970s–1980s sci-fi UI design — *Alien*, *Blade Runner*, *Star Trek*.

## License

GPL-2.0+ (for GTK compatibility), MIT for documentation
