[Storage](../Storage.md)
- [Data Logger](#data-logger)
  - [Setup](#setup)
    - [UDEV Configuration](#udev-configuration)
    - [Format](#format)
    - [Device Prep](#device-prep)
    - [Verify the Device](#verify-the-device)
  - [Requirements](#requirements)
  - [Devices](#devices)
    - [64GB USB Drive](#64gb-usb-drive)
    - [8TB USB Drive](#8tb-usb-drive)
- [Helpful Commands](#helpful-commands)
  - [See how much space is used on logger](#see-how-much-space-is-used-on-logger)

# Data Logger
Notes:
- Current crawler_app logs about 0.5 GB/min
## Setup
### UDEV Configuration
(Skip if already performed)
Setup a udev rule to mount the USB drive automatically.
1. Create a new UDEV rule:
```bash
sudo nano /etc/udev/rules.d/99-roslogs-automount.rules
```

2. Add these lines to the file:
```text
ACTION=="add", SUBSYSTEM=="block", ENV{ID_FS_LABEL}=="roslogs", RUN+="/usr/bin/systemd-mount --no-block --collect /dev/%k /mnt/usb_storage"
ACTION=="remove", SUBSYSTEM=="block", ENV{ID_FS_LABEL}=="roslogs", RUN+="/usr/bin/systemd-umount /mnt/usb_storage"
```

3. Save the file with Ctrl-X, then run the following to reload it:
```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```
### Format
1. Determine the appropriate drive mount:
```bash
lsblk
```
Look for output like `/dev/sdb`, `/dev/sdc`, etc and identify the partition number.
1. Run the following:
```bash
sudo umount /dev/sdb1`  # Or whatever you found in the above
sudo mkfs.ext4 -L "roslogs" /dev/sdb1
```

### Device Prep
Unplug the USB drive for 2 seconds, then plug back in and run the following:
```bash
sudo mkdir -p /mnt/usb_storage/datalogs
sudo chown -R $USER:$USER /mnt/usb_storage/datalogs
```

### Verify the Device
Run the following:
```bash
df -h /mnt/usb_storage
```
This should return a limit that matches the USB drive.

## Requirements
| Requirement | Description |
| ----------- | ----------- |

## Devices
### 64GB USB Drive

### 8TB USB Drive
Vectotech Rapid SSD
S/N: VT600044471

# Helpful Commands

## See how much space is used on logger
```bash
df -h /mnt/usb_storage
```