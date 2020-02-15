# Udev helpful commands

## List device attributes (and all parents attributes)
```
udevadm info -a -n /dev/{device}
```

## Test rules for a device (without running anything)
```
udevadm test $(udevadm info --query=path --name=/dev/{device}) 2>&1
```

keywords: ```udev; symlink;```
