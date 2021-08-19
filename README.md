# Widowx-arm-control-with-MoveIt
In this tutorial, Moveit will be used to control the widowx arm. MoveIt is the most widely used software for manipulation and has been used on over 150 robots. By incorporating the latest advances in motion planning, manipulation, 3D perception, kinematics, control and navigation, MoveIt is state of the art software for mobile manipulation.

# Install dependencies

"Htop" is a real-time process monitoring tool for Ubuntu operating system. The htop command is similar to top command, but much improved version.

$ sudo apt install git htop

"pcl-ros" package provides interfaces and tools for bridging a running ROS system to the Point Cloud Library

$ sudo apt install ros-kinetic-moveit ros-kinetic-pcl-ros

# Clone widowx_arm MoveIt repository and build

$ mkdir -p ~/widowx_arm/src

$ cd ~/widowx_arm/src

$ git clone https://github.com/Interbotix/widowx_arm.git

$ git clone https://github.com/Interbotix/arbotix_ros.git -b parallel_gripper

$ cd ~/widowx_arm

$ catkin_make

# ROS control of the arm independent of the SR300 (camera) Sensor

Give an access authorization for /dev/ttyUSB0

$ sudo chmod 777 /dev/ttyUSB0

$ cd ~/widowx_arm

$ source devel/setup.bash

$ roslaunch widowx_arm_bringup arm_moveit.launch sim:=false sr300:=false

This should load RVIZ with the proper WidowX arm bringup. You can use "planning" tab to move arm to different poses such as default pose with 0 value for all joints 
, alternate pose or valid random pose. You press update, then plan and execute to let motion planner plan for the path then execute this path.



