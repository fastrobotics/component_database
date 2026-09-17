[Compute](../Compute.md)
- [Raspberry Pi 4 Model B](#raspberry-pi-4-model-b)
- [OS Support](#os-support)
  - [ROS2 Installation Instructions](#ros2-installation-instructions)

# Raspberry Pi 4 Model B

# OS Support
| OS           | Comments                      |
| ------------ | ----------------------------- |
| Ubuntu 22.04 | Full Supported.  ROS2: Humble |
| Ubuntu 24.04 | Fully Supported.  ROS2: Jazzy |

## ROS2 Installation Instructions
1. Install Ubuntu 24.04 LTS onto SD Card with Raspberry Pi Imager
```bash
sudo apt install rpi-imager
```
- Select Ubuntu 24.04 Server
- Select OS Customization options:
    - Set Hostname
    - Set username/password: robot/*****
    - Enable ssh

2. Setup Locale:
```bash
locale
sudo apt update && sudo apt install -y locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale
```

3. Enable Ubuntu Universe Repository
```bash
sudo apt install -y software-properties-common
sudo add-apt-repository -y universe
```

4. Add the ROS 2 GPG Key and Repository
```bash
sudo apt update && sudo apt install -y curl gnupg
curl -sSL https://githubusercontent.com | gpg --dearmor | sudo tee /usr/share/keyrings/ros-archive-keyring.gpg > /dev/null
sudo chmod 644 /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://ros.org $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

5. Install ROS2 Jazzy
```bash
sudo rm -rf /var/lib/apt/lists/*
sudo apt update && sudo apt upgrade -y
sudo apt install -y ros-jazzy-ros-base
source /opt/ros/jazzy/setup.bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
```