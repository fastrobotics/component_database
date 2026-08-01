# UDEV Rules
sudo nano /etc/udev/rules.d/50-custom-usb.rules
```udev
# STMicroelectronics 151 IMU
SUBSYSTEM=="tty", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="5740", ATTRS{serial}=="?*", PROGRAM="/usr/bin/bash -c 'echo %s{serial} | tail -c 5'", SYMLINK+="imu_%s{manufacturer}_%c"

```
Then reload:
```bash
sudo udevadm control --reload-rules && sudo udevadm trigger
```
For IMU1: `/dev/imu_STMicroelectronics_3435`

# IMU 1:
```bash
udevadm info -a -n /dev/ttyACM0
```

david@DevComputer2:~/git/robot_framework$ udevadm info -a -n /dev/ttyACM0

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/tty/ttyACM0':
    KERNEL=="ttyACM0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0':
    KERNELS=="1-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{authorized}=="1"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bmCapabilities}=="2"

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{idProduct}=="5740"
    ATTRS{maxchild}=="0"
    ATTRS{devpath}=="1"
    ATTRS{urbnum}=="13"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{removable}=="removable"
    ATTRS{idVendor}=="0483"
    ATTRS{busnum}=="1"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{configuration}==""
    ATTRS{rx_lanes}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="67"
    ATTRS{tx_lanes}=="1"
    ATTRS{manufacturer}=="STMicroelectronics"
    ATTRS{product}=="STM32 Virtual ComPort"
    ATTRS{bcdDevice}=="0200"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{ltm_capable}=="no"
    ATTRS{speed}=="12"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{serial}=="375D36663435"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bmAttributes}=="c0"
    ATTRS{authorized}=="1"
    ATTRS{quirks}=="0x0"

  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{version}==" 2.00"
    ATTRS{rx_lanes}=="1"
    ATTRS{authorized_default}=="1"
    ATTRS{maxchild}=="16"
    ATTRS{manufacturer}=="Linux 5.15.0-139-generic xhci-hcd"
    ATTRS{urbnum}=="3500"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bMaxPower}=="0mA"
    ATTRS{devnum}=="1"
    ATTRS{interface_authorized_default}=="1"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{speed}=="480"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{devpath}=="0"
    ATTRS{bmAttributes}=="e0"
    ATTRS{idProduct}=="0002"
    ATTRS{ltm_capable}=="no"
    ATTRS{serial}=="0000:00:14.0"
    ATTRS{busnum}=="1"
    ATTRS{bcdDevice}=="0515"
    ATTRS{removable}=="unknown"
    ATTRS{tx_lanes}=="1"
    ATTRS{configuration}==""
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{authorized}=="1"
    ATTRS{quirks}=="0x0"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{idVendor}=="1d6b"

  looking at parent device '/devices/pci0000:00/0000:00:14.0':
    KERNELS=="0000:00:14.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{revision}=="0x10"
    ATTRS{irq}=="124"
    ATTRS{device}=="0xa36d"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{vendor}=="0x8086"
    ATTRS{consistent_dma_mask_bits}=="64"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{dbc}=="disabled"
    ATTRS{class}=="0x0c0330"
    ATTRS{local_cpus}=="ff"
    ATTRS{power_state}=="D0"
    ATTRS{subsystem_device}=="0x1264"
    ATTRS{enable}=="1"
    ATTRS{driver_override}=="(null)"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{ari_enabled}=="0"
    ATTRS{subsystem_vendor}=="0x1025"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{broken_parity_status}=="0"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{waiting_for_supplier}=="0"
