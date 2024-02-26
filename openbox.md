# Openbox

## Install
```bash
sudo pacman -S openbox
```

## Default configuration
```bash
mkdir -p ~/.config/openbox
cp /etc/xdg/openbox/{rc.xml,menu.xml,autostart,environment} ~/.config/openbox
```

## Background image
```bash
sudo pacman -S feh
nano .config/openbox/autostart

feh --bg-scale ${image-path} &

# Otra forma
feh --image-bg "#1D2021" --bg-center /home/prezdev/images/wallpaper.png
```

## obconf
```bash
sudo pacman -S obconf
```

## menumaker

 Genera menu.xml automáticamente según programas instalados

```bash
sudo pacman -S menumaker
mmaker -v -f OpenBox3
openbox --reconfigure
```

## dmenu (krunner like)
```bash
sudo pacman -S dmenu
nano .config/openbox/rc.xml
```

```xml
<keybind key="A-space">
  <action name="Execute">
    <command>dmenu_run</command>
  </action>
</keybind>
```

```bash
openbox --reconfigure
```

## thunar
```bash
sudo pacman -S thunar
```

## tint2

Panel básico

```bash
sudo pacman -S tint2
```

## lxqt-config (control panel))
```bash
sudo pacman -S lxqt-config
```

## red
```bash
sudo pacman -S network-manager-applet
```

### Añadir esto a .xinitrc
```bash
nm-applet &
```

## Look and feel (themes)
```bash
sudo pacman -S lxappearance arc-gtk-theme
```

## Preferencias de energía
```bash
sudo pacman -S xfce4-power-manager
```

## Ícono de volumen en panel (Sólo escoger uno)
```bash
sudo pacman -S volumeicon
sudo pacman -S pasystray
```

## Extractor de zip gráfico
```bash
sudo pacman -S file-roller
```

## Ver particiones ntfs
```bash
sudo pacman -S ntfs-3g
```

## Audio (sólo en notebook t14)
```bash
sudo pacman -S sof-firmware
sudo pacman -S alsa-utils alsa-plugins pulseaudio pulseaudio-alsa pavucontrol
pulseaudio --start
reboot
pavucontrol
```

## Colorpicker
```bash
sudo pacman -S colorpicker
```

## Clipboard
```bash
sudo pacman -S clipit
```

## Flameshot
```bash
sudo pacman -S flameshot
```

### Keybinding flameshot in openbox
```bash
nano ~/.config/openbox/rc.xml
```

```xml
<keybind key="Print">
  <action name="Execute">
    <command>flameshot gui</command>
  </action>
</keybind>
```

```bash
openbox --reconfigure
```

## .xinitrc
```bash
tint2 &
nm-applet &
pasystray &
conky &
clipit &
flameshot &
setxkbmap -layout es
exec openbox-session
```

## Montar manual con udisks2
```bash
sudo pacman -S udisks2

# Listado de dispositivos
lsblk

udisksctl mount -b /dev/sdc1
udisksctl unmount -b /dev/sdc1
```

## montar con gui (udiskie). udisks2 requerido
```bash
sudo pacman -S udiskie

# .xinitrc
udiskie --tray &
```

## Gestor de notificaciones Dunst
```bash 
sudo pacman -S dunst

# Archivo de configuración
mkdir -p ~/.config/dunst && echo -e "[global]\nfont = Sans 15" > ~/.config/dunst/dunstrc 

# .xinitrc
dunst &

# Prueba con una notificación
notify-send "Prueba de Notificación" "Esta es una prueba de notificación."
```

## picom
```bash
sudo pacman -S picom
sudo mv /etc/xdg/picom.conf /etc/xdg/picom.conf.bak
sudo nano /etc/xdg/picom.conf
```

```bash
# Shadows
shadow = true;
shadow-radius = 8;
shadow-opacity = 0.6;
shadow-offset-x = -3;
shadow-offset-y = -3;
shadow-exclude = [
  "class_g ?= 'i3-frame'"
];
# Fading
fading = true;
fade-in-step = 0.03;
fade-out-step = 0.03;
fade-delta = 4;
# Transparency / Opacity
inactive-opacity = 1;
frame-opacity = 1.0;
inactive-opacity-override = false;
detect-client-opacity = true;
focus-exclude = [ "class_g = 'Cairo-clock'" ];
opacity-rule = [
  "90:class_g = 'URxvt'",
  "97:class_g = 'Anki'",
  "70:class_g = 'i3bar'"
];
# General settings
backend = "glx";
vsync = true;
mark-wmwin-focused = true;
mark-ovredir-focused = true;
detect-rounded-corners = true;
detect-client-opacity = true;
# refresh-rate = 75;
use-ewmh-active-win = true;
detect-transient = true;
detect-client-leader = true;
use-damage = true;
log-level = "warn";
wintypes:
{
  tooltip = { fade = true; shadow = true; opacity = 1; focus = true; full-shadow = false; };
  dock = { shadow = false; opacity: 0.8; }
  dnd = { shadow = false; }
  popup_menu = { opacity = 0.8; }
  dropdown_menu = { opacity = 1; }
};
unredir-if-possible = false;

blur-background = true;
blur-method = "dual_kawase";
blur-strength = 1;
```

### picom in .xinitrc
```bash
picom &
```

## Temas de openbox
```bash
yay -S openbox-themes
```

## Instalación de íconos
```bash
yay -S emerald-icon-theme el-general-icon-theme-git humanity-icon-theme la-capitaine-icon-theme nitrux-icon-theme win11-icon-theme-git windows-xp-icon-theme windows10-icon-theme arc-icon-theme adwaita-icon-theme
```

## Calendario en tint2
```bash
yay -S orage gsimplecal
nano .config/tint2/tint2rc
clock_lclick_command = gsimplecal
```