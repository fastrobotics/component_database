# ROS 2 Jazzy Installation Guide for NVIDIA Jetson Orin Nano

This guide walks you through setting up **ROS 2 Jazzy Jalisco** on an **NVIDIA Jetson Orin Nano**. 

---

## 1. System Requirements & Preparation

Before starting, ensure your system is up to date and your locale supports UTF-8.

```bash
# Update the system package list
sudo apt update && sudo apt upgrade -y

# Install and configure UTF-8 locales
sudo apt install locales -y
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

---

## 2. Set Up Sources

You need to authorize the ROS 2 GPG keys and add the required repositories.

```bash
# Enable the Ubuntu Universe repository
sudo apt install software-properties-common -y
sudo add-apt-repository universe -y

# Download and add the ROS 2 GPG key
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros2/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# Add the repository to your sources list
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.p/ros2.list > /dev/null
```

---

## 3. Install ROS 2 Jazzy Packages

Once the repositories are linked, fetch the metadata and install the core framework packages.

```bash
# Update your repository caches
sudo apt update

# Install the ROS Base framework (recommended for headless Jetson systems)
sudo apt install ros-jazzy-ros-base -y

# Install build tools, colcon compilation suite, and dependencies tracker
sudo apt install -y python3-colcon-common-extensions python3-rosdep python3-argcomplete
```

---

## 4. Environment Configuration

To ensure every new terminal window knows where your ROS 2 ecosystem lives, configure your shell profile.

```bash
# Automatically source ROS 2 and colcon autocomplete on login
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
source ~/.bashrc

# Initialize rosdep to manage workspace dependencies
sudo rosdep init
rosdep update
```

---

## 5. Verify Installation

Test that your installation is functional by printing out the current environment settings:

```bash
printenv | grep -i ROS
```
