[Compute](../Compute.md)

# Nvidia Jetson Orin Nano Dev Kit
![](artifacts/NvidiaJetsonOrinNano.jpg)
# OS Support
| OS           | Comments  |
| ------------ | --------- |
| Ubuntu 22.04 | Jetpack 6 |
| Ubuntu 24.04 | Jetpack 7 |

# Configuration
For Crawler/Robot Framework, known as a `GPUModule`

# Questions
- What is the architecture?  What do I need to modify in build scripts?
- How to take advantage of GPU?

# Setup
## Impage Preparation
- Download Jetpack Release: https://developer.nvidia.com/embedded/jetpack/downloads

## Image SD Card
- Use `balena-etcher` to copy Jetpack ISO to SD Card

## Harware Setup
Do Monitor based setup in quick-start guide

## SW Updates

# Command Outputs
**lsb_release -a**
```bash
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.4 LTS
Release:	24.04
Codename:	noble
```

**uname -m**
```bash
aarch64
```

**sudo apt-cache show nvidia-jetpack | grep "Version"**
```bash
Version: 7.2.1-b49
Version: 7.2-b187
Version: 7.2-b184
```
# References
- [Jetson Quick Start](https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/latest/quick_start.html)
- [Headless Setup](artifacts/jetson_orin_nano_headless_setup.md)
- [ROS2 Install Guide](artifacts/jetson_orin_nano_ros2_jazzy_guide.md)
