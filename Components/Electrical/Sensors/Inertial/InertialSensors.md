[Sensors](../Sensors.md)

- [Inertial Sensors](#inertial-sensors)
  - [ToDo](#todo)
- [Sensors to Consider:](#sensors-to-consider)
- [Sensor: NavX MXP IMU](#sensor-navx-mxp-imu)
- [Sensor: Sparkfun 9DoF Razor IMU](#sensor-sparkfun-9dof-razor-imu)
  - [Device Mapping](#device-mapping)
  - [Getting Started](#getting-started)
    - [Setup](#setup)
- [Sensor: Adafruit LSM9DS0](#sensor-adafruit-lsm9ds0)
- [Sensor: Robotshop TM151](#sensor-robotshop-tm151)
  - [Device Mapping](#device-mapping-1)

# Inertial Sensors

## ToDo
| Vendor |
| ------ |
| Pololu |

[IMU Comparison](IMUComparison.ods)

# Sensors to Consider:
- https://www.adafruit.com/product/4569
- https://www.robotshop.com/products/seeedstudio-seeed-studio-xiao-nrf52840-sense-tinyml-tensorflow-lite-imu-microphone-bluetooth-50?qd=be9ed18ce3b530086f5fd6a5c492fdfa
- https://www.robotshop.com/products/transducerm-ahrs-9-axis-imu-for-robotics-autonomous-vehicles-tm151-tm171?qd=be9ed18ce3b530086f5fd6a5c492fdfa
- https://www.robotshop.com/products/minimu-9-v5-gyro-accelerometer-compass-lsm6ds33-and-lis3mdl-carrier?qd=985966b43b18b668417c8e7b67767b15
- https://www.robotshop.com/products/bno055-9-dof-absolute-orientation-imu-module?qd=5663b996792c9f9e5b030270d4d7dd69
- https://www.robotshop.com/products/yahboom-yahboom-imu-sensor-module-ahrs-support-ros1-ros2-jetson-raspberry-pi-10-axis-imu?qd=5663b996792c9f9e5b030270d4d7dd69
- https://www.pololu.com/product/2862
# Sensor: NavX MXP IMU

![](NavXIMU/NavXIMU.png)

[User Guide](NavXIMU/UserGuide.pdf)

# Sensor: Sparkfun 9DoF Razor IMU
![](9DoFRazorIMU/9DoFRazorIMU.jpg)

[Vendor Link](https://learn.sparkfun.com/tutorials/9dof-razor-imu-m0-hookup-guide/all)

[User Guide](9DoFRazorIMU/UserGuide.pdf)

[Data Sheet](9DoFRazorIMU/DataSheet.pdf)

## Device Mapping
For Raspberry Pi 4, there is a custom udev rule that looks for the proper vendor and product information, and then auto-creates a symlink to the device.  See [UDev Analysis](9DoFRazorIMU/UDevAnalysis.md) for more information.

Current supported IMU's (on-hand):
| IMU                                                  | Device Name              | Analysis Report                                                        |
| ---------------------------------------------------- | ------------------------ | ---------------------------------------------------------------------- |
| [Sparkfun 183F IMU](9DoFRazorIMU/IMU_Sparkfun_183F/) | `/dev/imu_SparkFun_183F` | [report](9DoFRazorIMU/IMU_Sparkfun_183F/analysis/IMU_Sparkfun_183F.md) |
| IMU2                                                 | `/dev/imu_SparkFun_2115` |



## Getting Started
### Setup
Perform the following:
```bash
sudo apt install minicom
sudo usermod -a -G dialout $USER

```


# Sensor: Adafruit LSM9DS0

# Sensor: Robotshop TM151
![](RobotshopTM151/RobotshopTM151.png)

[Vendor Link](https://www.robotshop.com/products/transducerm-ahrs-9-axis-imu-for-robotics-autonomous-vehicles-tm151-tm171?srsltid=AfmBOoqOG8qVXYtEs8XnNk-hWy95FQ71PhYior65ziFs_HUChezgHLE8)

[User Guide](RobotshopTM151/TransducerM_TM100-200_UserGuide_EN_V131.pdf)

[Sample Code](RobotshopTM151/TransducerM_Lib_Protocol_CPP/)

## Device Mapping
For Raspberry Pi 4, there is a custom udev rule that looks for the proper vendor and product information, and then auto-creates a symlink to the device.  See [UDev Analysis](RobotshopTM151/UDevAnalysis.md) for more information.

Current supported IMU's (on-hand):
| IMU  | Device Name                        |
| ---- | ---------------------------------- |
| IMU1 | `/dev/imu_STMicroelectronics_3435` |