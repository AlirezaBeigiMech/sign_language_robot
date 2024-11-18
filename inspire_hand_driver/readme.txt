# Inspire Robot ROS Package

The `inspire_robot` package enables the use of Inspire Robotics Company's dexterous hands and mechanical grippers on the ROS platform. This package has been tested only on the ROS Kinetic environment. Testing in other ROS environments is pending.

## Prerequisites

Before using this package, ensure the following environment setup steps are completed (required only for the first use):

```bash
# 1. Install ROS Kinetic
# 1.1 Configure Ubuntu's repository settings
# Enable "restricted," "universe," and "multiverse."

# 1.2 Add the ROS sources list
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

# 1.3 Add the key
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

# Alternatively:
curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -

# 1.4 Update and install ROS Kinetic
sudo apt-get update
sudo apt-get install ros-kinetic-desktop-full

# 1.5 Initialize rosdep
sudo rosdep init
rosdep update

# 1.6 Configure the environment
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc

# 1.7 Install build dependencies
sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential

# 2. Create a Catkin Workspace
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
catkin_init_workspace
cd ~/catkin_ws
catkin_make
source devel/setup.bash

# 3. Add `inspire_robot` Package
# Place `inspire_robot.zip` in the `~/catkin_ws/src` directory and unzip
cd ~/catkin_ws/src
unzip inspire_robot.zip

# Install package dependencies
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y

# Compile the package
catkin_make
