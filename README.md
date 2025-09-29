<img src="https://moveit.ros.org/assets/logo/moveit2/moveit_logo-black.png" alt="MoveIt 2 Logo" width="200"/>

The MoveIt Motion Planning Framework for **ROS 2**. For ROS 1, see [MoveIt 1](https://github.com/ros-planning/moveit).

*Easy-to-use open source robotics manipulation platform for developing commercial applications, prototyping designs, and benchmarking algorithms.*

## Continuous Integration Status

[![Formatting (pre-commit)](https://github.com/ros-planning/moveit2/actions/workflows/format.yaml/badge.svg?branch=main)](https://github.com/ros-planning/moveit2/actions/workflows/format.yaml?query=branch%3Afoxy)
[![CI (Foxy)](https://github.com/ros-planning/moveit2/actions/workflows/ci.yaml/badge.svg?branch=foxy)](https://github.com/ros-planning/moveit2/actions/workflows/ci.yaml?query=branch%3Afoxy)
[![Code Coverage](https://codecov.io/gh/ros-planning/moveit2/branch/foxy/graph/badge.svg?token=W7uHKcY0ly)](https://codecov.io/gh/ros-planning/moveit2)

## General MoveIt Documentation

- [MoveIt Website](http://moveit.ros.org)
- [Tutorials and Documentation](https://ros-planning.github.io/moveit_tutorials/)
- [How to Get Involved](http://moveit.ros.org/about/get_involved/)
- [Future Release Dates](https://moveit.ros.org/#release-versions)

## MoveIt 2 Specific Documentation

- [MoveIt 2 Migration Progress](https://docs.google.com/spreadsheets/d/1aPb3hNP213iPHQIYgcnCYh9cGFUlZmi_06E_9iTSsOI/edit?usp=sharing)
- [MoveIt 2 Migration Guidelines](doc/MIGRATION_GUIDE.md)
- [MoveIt 2 Development Roadmap](https://moveit.ros.org/documentation/contributing/roadmap/)

## Source Build

See [MoveIt 2 Source Build - Linux](https://moveit.ros.org/install-moveit2/source/)

## Getting Started

We've prepared a simple demo setup that you can use for quickly spinning up a simulated robot environment with MoveItCpp.
See the [run_moveit_cpp](moveit_demo_nodes/run_moveit_cpp) demo package for further instructions and information.

The package [run_move_group](moveit_demo_nodes/run_move_group) provides a simple launch file for running a MoveGroup setup.
You can test it using the MotionPlanning display in RViz or by implementing your own MoveGroupInterface application.

## Having Doxygen Reference Locally
See [How To Generate API Doxygen Reference Locally](https://moveit.picknik.ai/main/doc/how_to_guides/how_to_generate_api_doxygen_locally.html)

## Prerequisites & System Requirements

### System Specifications
- OS: Ubuntu 20.04 LTS
- ROS Distribution: ROS 2 Foxy Fitzroy
- Build Time: ~5-6 minutes on modern hardware
- Disk Space: ~2GB for source + build artifacts

### Core Dependencies Installation
```
# Update system packages
sudo apt update && sudo apt dist-upgrade -y

# Install build essentials
sudo apt install -y \
  build-essential \
  cmake \
  git \
  python3-colcon-common-extensions \
  python3-flake8 \
  python3-rosdep \
  python3-setuptools \
  python3-vcstool \
  wget

# Update rosdep database
rosdep update
```

### Critical Foxy-Specific Dependencies
Key Issue: Foxy requires additional system-level dependencies not automatically resolved by rosdep.

1. Install System Libraries
```
# Install KDL and OMPL system libraries
sudo apt install -y \
  liborocos-kdl-dev \
  libompl-dev
```
Rationale: These libraries are required for kinematics and motion planning but may not be available through rosdep in Foxy.

2. Install ROS Testing Framework
```
# Critical for build success
sudo apt install -y ros-foxy-ros-testing
```

3. Install Warehouse Dependencies
```
# Install warehouse ROS packages
sudo apt install -y ros-foxy-warehouse-ros
```

## Verification & Testing
- Verify Installation
```
# Check if MoveIt2 packages are available
ros2 pkg list | grep moveit

# Launch basic demo (if available)
ros2 launch moveit2_tutorials demo.launch.py
```