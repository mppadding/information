# Udev helpful commands

## List device attributes (and all parents attributes)
```
udevadm info -a -n /dev/{device}
```

keywords: ```udev; attributes; /dev/```

## Test rules for a device (without running anything)
```
udevadm test $(udevadm info --query=path --name=/dev/{device}) 2>&1
```

keywords: ```udev; symlink; test udev```

## List all devices by dev name and their corresponding real name
```
for sysdevpath in $(find /sys/bus/usb/devices/usb*/ -name dev); do
    (
        syspath="${sysdevpath%/dev}"
        devname="$(udevadm info -q name -p $syspath)"
        [[ "$devname" == "bus/"* ]] && continue
        eval "$(udevadm info -q property --export -p $syspath)"
        [[ -z "$ID_SERIAL" ]] && continue
        echo "/dev/$devname - $ID_SERIAL"
    )
done
```

keywords: ```udev; symlink; list devices; /dev/```
