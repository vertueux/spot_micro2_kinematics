Spot Micro Kinematics is a C++ library created to handle operations on the Spot Micro 2 Project. There are no external dependencies like eigen3 or another C++ math library needed.
This project is still in test phase and uses `std::vector` to create matrices.

> **Here are the last steps to complete in order to enter a stable version of this repository:**
> * Program an algorithm to find the inverse of a 4x4 matrix based on the std::vector
> * Run tests to verify that the entire program is working properly


# Dependencies 
* Have [ROS2](https://ros.org) installed
* Have ```python3-colcon-common-extensions``` installed 

# Set locale
Make sure you have a locale which supports ```UTF-8```. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.
```bash
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

# Setup Sources
You will need to add the ROS 2 apt repository to your system. First, make sure that the [Ubuntu Universe repository](https://help.ubuntu.com/community/Repositories/Ubuntu) is enabled by checking the output of this command.
```bash
apt-cache policy | grep universe
```
This should output a line like the one below:
```bash
500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
    release v=22.04,o=Ubuntu,a=jammy,n=jammy,l=Ubuntu,c=universe,b=amd64
```
If you don’t see an output line like the one above, then enable the Universe repository with these instructions.
```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```
Now add the ROS 2 apt repository to your system. First authorize our GPG key with apt.
```bash
sudo apt update && sudo apt install curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
Then add the repository to your sources list.
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

# Install ROS 2 packages
Update your apt repository caches after setting up the repositories.
```bash
sudo apt update
```
ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.
```bash
sudo apt upgrade
```
Desktop Install (Recommended): ROS, RViz, demos, tutorials.
```bash
sudo apt install ros-humble-desktop
```
ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.
```bash
sudo apt install ros-humble-ros-base
```

# Environment setup
## Sourcing the setup script
Set up your environment by sourcing the following file.
```bash
source /opt/ros/humble/setup.bash
```

# Installing colcon
```bash
sudo apt install python3-colcon-common-extensions
```
# Clone & Build it 
You can clone and run this package by copying the commands below:  

```bash
git clone https://github.com/vertueux/spot_micro_kinematics.git
colcon build --packages-select spot_micro_kinematics
```

# LICENSE
```
MIT License

Copyright (c) 2022 Virtuous

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```