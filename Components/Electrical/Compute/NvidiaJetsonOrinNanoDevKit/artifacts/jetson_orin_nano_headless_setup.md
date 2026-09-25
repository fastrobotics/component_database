# Headless Setup and ROS 2 Jazzy Installation Guide
### NVIDIA Jetson Orin Nano Development Workspace

This document provides a comprehensive, step-by-step workflow for configuring your **NVIDIA Jetson Orin Nano** entirely **headless** (without a monitor, keyboard, or mouse) using an **Ubuntu host computer**, converting it into a lean server environment, and installing **ROS 2 Jazzy**.

---

## Phase 1: Operating System Installation & Pre-Configuration

To build a headless setup, you must bypass the standard graphical first-boot wizard. Choose **one** of the two native Ubuntu host methods below to configure your user account before or during the first boot.

### Method A: Pre-configuring using NVIDIA SDK Manager (Recommended)
This method lets you define your credentials directly on your Ubuntu host PC before flashing.

1. **Install SDK Manager on your Ubuntu Host PC:**
   Download the official `.deb` installer from NVIDIA and install it via terminal:
   ```bash
   sudo apt update
   sudo apt install ./sdkmanager_*_amd64.deb -y
   ```
2. **Launch and Log In:** Open `sdkmanager` from your terminal or applications menu and log into your NVIDIA developer account.
3. **Hardware Selection:** Select **Jetson Orin Nano Developer Kit** and your desired **JetPack** version.
4. **Bypass the First-Boot Wizard:** When advancing to the step right before flashing, locate the **OEM Configuration** dropdown menu.
   * Change it from **Runtime** to **Preconfig**.
   * Enter your desired **Username** and **Password** directly into the setup fields.
5. **Flash the Target:** Insert your storage media (MicroSD or NVMe SSD) or put the Jetson into Recovery Mode via USB-C to complete the flash process.
6. **Network Boot:** Once finished, insert the storage into your Jetson, connect an **Ethernet cable**, and power it on. It will automatically boot straight to your local network.

### Method B: The USB-C Virtual Serial Terminal (Alternative)
If you flashed a stock JetPack image via BalenaEtcher or `dd`, you can interact with the hidden text-based system wizard over a USB cable.

1. **Connect Cables:** Insert the flashed storage into the Jetson. Connect an **Ethernet cable** to your network router, and a **USB-C data cable** directly from the Jetson's USB-C port to your Ubuntu host PC.
2. **Power On:** Plugin the Jetson Orin Nano's power supply.
3. **Identify the Serial Interface:** Open a terminal on your Ubuntu host PC and check for the virtual serial connection:
   ```bash
   ls /dev/ttyACM*
   ```
   *(Usually registers as `/dev/ttyACM0` or `/dev/ttyACM1`)*
4. **Access the Text Setup Wizard:** Connect to the serial line using `screen`:
   ```bash
   sudo apt install screen -y
   sudo screen /dev/ttyACM0 115200
   ```
5. **Complete Wizard:** Press **Enter** to wake up the prompt. Complete the step-by-step terminal wizard to set language, keyboard layouts, and create your custom **Username** and **Password**.
6. **Exit Screen:** When the system begins rebooting, exit the utility by typing `Ctrl + A`, followed by `:quit`.

---

## Phase 2: Remote Connection & Server Optimization

### Locating your Jetson on the Network
If you do not know the IP address assigned to your Jetson by your router, you can scan your local subnet from your Ubuntu host PC:
```bash
sudo apt install nmap -y
sudo nmap -sn 192.168.1.0/24  # Adjust to match your local router gateway
```
Look for an IP address registered to **NVIDIA** or **Telegra**. 

### Connecting via SSH
Log in directly from your Ubuntu terminal:
```bash
ssh username@jetson_ip_address
```

### Optimizing into an "Ubuntu Server" Layout
Standard JetPack boots a complete Ubuntu Desktop GUI, consuming substantial system RAM and CPU. To convert your environment into a headless server structure, disable the display manager:

1. **Change System Default Target to Text-Only Mode:**
   ```bash
   sudo systemctl set-default multi-user.target
   ```
2. **Reboot the Jetson:**
   ```bash
   sudo reboot
   ```
*Note: If you ever need to reverse this back to a desktop setup in the future, run: `sudo systemctl set-default graphical.target`*

---

## Phase 3: Step-by-Step ROS 2 Jazzy Installation

Once your lean server environment is online and updated, log back in via SSH to deploy **ROS 2 Jazzy**.

### 1. System Localization & Environment Configurations
Ensure your terminal environment supports UTF-8 encoding:
```bash
sudo apt update && sudo apt install locales -y
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

### 2. Enable Ubuntu Repositories & Keyrings
Add the official ROS 2 GPG keys and package repositories to your apt configurations:
```bash
sudo apt install software-properties-common curl -y
sudo add-apt-repository universe -y

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### 3. Core Package Installation
Update your repository indexes and pull down the base ROS 2 system:
```bash
sudo apt update
sudo apt install ros-jazzy-ros-base -y
```

### 4. Development Tools & Build Infrastructure
Install package dependencies along with `colcon` to handle compiling workspaces:
```bash
sudo apt install -y python3-colcon-common-extensions python3-rosdep python3-argcomplete
```

### 5. Automated Environment Sourcing
Permanently inject the ROS environment setup variables into your login shell profile:
```bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
source ~/.bashrc
```

### 6. Rosdep Database Initialization
Initialize the ROS package tracking index to simplify dependency resolution down the road:
```bash
sudo rosdep init || true
rosdep update
```

---

## Phase 4: Basic Verification

To confirm your headless workspace and ROS 2 ecosystem are functioning as intended, run a basic node check.

1. In your primary SSH terminal, spin up a demo publisher node:
   ```bash
   ros2 run demo_nodes_cpp talker
   ```
2. Open a separate terminal window on your Ubuntu host PC, SSH back into your Jetson, and monitor the incoming topics:
   ```bash
   ros2 run demo_nodes_py listener
   ```
If you see the speaker publishing data and the listener reading it successfully, your ROS 2 Jazzy workspace is fully configured on your headless Orin Nano!
