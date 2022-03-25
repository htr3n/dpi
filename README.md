  # DPI Calculator for X

  ## File `~/.xsession`

```conf
# Target DPI
dpi=122
# For applications supporting XSettings, `Xft/DPI' sets font scaling
# (and sometimes interface scaling), `Gdk/WindowScalingFactor' sets
# interface scaling with GTK 3, and `Gdk/UnscaledDPI' undo font scaling
# for GTK 3 applications.
> ~/.xsettingsd cat <<EOF
Xft/DPI $(( $dpi*1024 ))
Gdk/WindowScalingFactor $(( $dpi/96 ))
Gdk/UnscaledDPI $(( $dpi*1024/($dpi/96) ))
EOF

pkill -HUP xsettingsd || xsettingsd &

# For QT applications.
export QT_AUTO_SCREEN_SCALE_FACTOR=1

# For miscellaneous applications.
echo Xft.dpi: $dpi | xrdb -merge
```

## File `~/.xsettingsd`

```conf
Xft/Hinting 0
Xft/RGBA "rgb"
Xft/HintStyle "hintnone"
Xft/Antialias 0

Gtk/CursorThemeSize 0
Gtk/FontName "SF Display Text 9"
Gtk/IconThemeName "Yaru"
Gtk/MenuBarAccel "F10"
Gtk/MenuImages 1
Gtk/ToolbarIconSize 3
Gtk/ToolbarStyle "icons"

Xft/DPI 121196
Gdk/WindowScalingFactor 1.5
Gdk/UnscaledDPI 80797
```
