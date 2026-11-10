# VectorFlux — KDE Plasma Installation

## Prerequisites
- GTK4 theme files go in `~/.themes/VectorFlux/gtk/` or `~/.local/share/themes/VectorFlux/gtk/`
- Plasma colourscheme file goes in `~/.local/share/color-schemes/VectorFlux.colorscheme`

## Step 1: Install the Colourscheme

```bash
mkdir -p ~/.local/share/color-schemes
cp kde/colorschemes/VectorFlux.colorscheme ~/.local/share/color-schemes/
```

## Step 2: Install GTK Theme (for KDE apps using GTK)

```bash
mkdir -p ~/.local/share/themes/VectorFlux/gtk
cp gtk/4.0/* ~/.local/share/themes/VectorFlux/gtk/
```

## Step 3: Apply in System Settings

1. Open **System Settings** → **Appearance**
2. Under **Colors**, select **VectorFlux** from the dropdown
3. Under **Style**, select **Breeze** (recommended — VectorFlux pairs with Breeze)
4. Under **Windows**, pick a window decoration theme you like

## Optional: Enable for All GTK Apps

To make VectorFlux the default for GTK3/GTK4 applications everywhere:

```bash
# GTK3
mkdir -p ~/.config/gtk-3.0
cat > ~/.config/gtk-3.0/settings.ini << EOF
[Settings]
gtk-theme-name=VectorFlux
gtk-application-prefer-dark-theme=false
EOF

# GTK4 (uses XDG_CONFIG_HOME/gtk)
mkdir -p ~/.config/gtk-4.0
cp gtk/4.0/* ~/.config/gtk-4.0/
```

## Dark Mode (Plasma 6 / KDE Plasma ≥6)

Set the system colour scheme to use dark:
```bash
# In System Settings → Appearance → Colors
#   Select "VectorFlux"
# Then toggle under System → General → Color Scheme Variant → Dark
```

Or force it via `kwriteconfig5`:
```bash
kwriteconfig5 --file kdeglobals \
  --group "Colors:Window Dark" \
  --key BackgroundNormal "#15151a"
```

## Testing

Test the colourscheme with:
```bash
# Open System Settings → Look and Feel → Colors
# Or launch a KDE app:
dolphin & kate & systemsettings &
```

## Uninstalling

```bash
rm ~/.local/share/color-schemes/VectorFlux.colorscheme
rm -rf ~/.local/share/themes/VectorFlux/
rm -f ~/.config/gtk-3.0/settings  # if you made it
# Revert GTK4: rm -rf ~/.config/gtk-4.0/
```

