# i3
i3 Fenstermanager installieren und anpassen.
## 1. Installation der benötigten Pakete
```
sudo pacman -S i3 i3-gaps i3lock xorg lxappearance nitrogen nautilus firefox dmenu ttf-font-awesome polkit alsa-utils pulseaudio-alsa pulseaudio speedtest-cli alacritty
yay -S ly j4-dmenu-desktop bumblebee-status ulauncher
```
Falls `dmenu` nicht funktionieren sollte nutzen sie folgende Befehle.
```
sudo nano /etc/locale.gen
sudo locale-gen
sudo localectl set-locale LANG=de_DE.UTF-8
```
```
cp alacritt.yml ~/.config/
```
Sollten Kontextmenüs durchichtig sein, kopieren sie sich die `picom.conf`von `/etc/xdg/picom.conf`nach `~/.config`und entfernen sie aus der letzten Sektion `tooltip`, `popup_menu` und `dropdown_menu`.
</br>

## 2. Konfiguration
Mod-Taste festlegen und Mausfokus konfigurieren mit `set $mod Mod4` und `focus_follows_mouse no`. Schriftarten festlegen mit `font pango:Ubuntu Regular, FontAwesome 12`.
```
bindsym $mod+t exec alacritty
bindsym $mod+e exec nautilus
bindsym $mod+d exec --no-startup-id /bin/j4-dmenu-desktop
bindsym $mod+space exec --no-startup-id /bin/ulauncher
```
> Tastenkürzel für Programme
</br>

```
bindsym $mod+Left focus left
bindsym $mod+Down focus down
bindsym $mod+Up focus up
bindsym $mod+Right focus right
```
> fokusiertes Fenster ändern
</br> 

```
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right
```
> fokusiertes Fenster verschieben
</br>

```
bindsym $mod+h split h
bindsym $mod+v split v
```
> neues Fenster horizontal/vertikal öffnen
</br> 

```
bar {
	status_command /usr/share/bumblebee-status/bumblebee-status \
	-t greyish-powerline \
	-m speedtest nic cpu memory disk pasink battery datetime \
	-p nic.format: '{ssid} - {ip}' \
	-p datetime.format: strftime"%d.%m. %H:%M:%S " \
	-p brightness.use_acpi \

colors {
    background #4d4d4d
    statusline $white
    focused_workspace #0082e6 #0082e6 #000000
    active_workspace #000000 #4d4d4d #4d4d4d
    inactive_workspace #4d4d4d #666666 #ffffff
    urgent_workspace #d33682 #d33682 #fdf6e3
    }
}
```
> Bumblebee Statusleiste