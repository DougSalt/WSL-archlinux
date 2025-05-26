# WSL-archlinux

Instructions for setting up archlinux for GUI use in WSL2
```bash
pacman -S xorg-server xorg-wayland xorg-xeyes gnome-desktop dbus
systemctl start dbus
```
Make sure a `.bashrc` is called from `~/.bash_profile` thus
```bash
if [[ -f ~/.bashrc ]]
then
        . ~/.bashrc
fi
```
Add the following to the .bashrc
```bash
export DISPLAY=/mnt/wslg/.X11-unix/X0
export WAYLAND_DISPLAY=wayland-0
if command -v dbus-launch >/dev/null 2>&1 && [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
    eval "$(dbus-launch --sh-syntax)"
fi
```
