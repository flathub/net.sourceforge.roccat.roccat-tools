# Roccat-tools

You can read these instruction online at https://github.com/flathub/net.sourceforge.roccat.roccat-tools.

## Add udev rules for your devices.

1. List supported devices rules :

```sh
flatpak run --command="ls" net.sourceforge.roccat.roccat-tools /app/lib/udev
```

2. Copy the rules correponding to your devices(s) to your host system. For instance :

```sh
DEVICE=[YOUR_DEVICE] && flatpak run --command="cat" net.sourceforge.roccat.roccat-tools /app/lib/udev/90-roccat-${DEVICE}.rules | sed -e 's/, GROUP="roccat"//g' -e 's/MODE="0660"/MODE="0666"/g' | sudo tee /etc/udev/rules.d/90-roccat-${DEVICE}.rules
```

replace `[YOUR_DEVICE]` with your device. e.g : `DEVICE=tyon && flatpak [...]`

3. Reload udev rules

```sh
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Start your device application

You can now start a roccat configuration application from your desktop environment.

Be sure to start the configuration app for your configured device.
