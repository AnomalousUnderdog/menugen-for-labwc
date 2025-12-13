# Labwc/Openbox Menu Generator

## Features

- **Dual Mode**: Generate static XML menus or dynamic piped menus (Openbox).
- **Robust Icon Detection**: Automatically finds the best icon by reading the GTK icon theme from `~/.config/gtk-3.0/settings.ini`.
- **Pretty Formatting**: Outputs clean static XML.
- **Custom Footer**: Supports a customizable footer with dynamic icons and separators.
- **Auto-Reconfigure**: Can automatically reconfigure Labwc after generating the menu.

## Important Notes on Icons

⚠️ Icon Search Paths

This script currently looks for icons in `/usr/share/icons`. It does not search `~/icons` or `~/.local/share/icons`.

If your `settings.ini` specifies a theme (e.g., "Papirus") that is installed locally in your home folder, the icons will not appear in the menu. Please ensure your desired icon theme is installed system-wide in `/usr/share/icons`.

## Usage

### Generate Static Menu
```bash
python3 menu-generator.py -o ~/.config/labwc/menu.xml
```

### Disable Footer
```bash
python3 menu-generator.py -o ~/.config/labwc/menu.xml -f false
```

## Preview

### Labwc (Static Menu)

| | |
|-|-|
|![](/preview/labwc.png)|![](/preview/labwc1.png)

### Openbox (Piped Menu)

| | |
|-|-|
|![](/preview/menu.png)|![](/preview/menu2.png)

`menu.xml` for the openbox menu shown above
```
<?xml version="1.0" encoding="UTF-8"?>
<openbox_menu>
    <menu id="root-menu" label="Root Menu">
        <menu id="apps-menu"
              label="Applications (Dynamic)"
              icon="/usr/share/icons/Papirus/48x48/categories/applications-all.svg"
              execute="python3 /path/to/menu-generator.py" /> <!-- Edit this line -->
<!-- menu without footer: "python3 /path/to/menu-generator.py -f false" -->

        <item label="Exit" icon="/usr/share/icons/Tela/32/status/system-log-out.svg">
            <action name="Exit"/>
        </item>
    <item label="Terminal" icon="" execute="xfce4-terminal">
    </item>
    </menu>
</openbox_menu>
```

## Configuration

1. Edit the `footer_items` list in the script to customize menu footer entries with your preferred applications and icons.
2. Edit `terminal_string` to set your preferred terminal emulator.

## Credits

Original work by [onuronsekiz](https://github.com/onuronsekiz/obamenu/)
