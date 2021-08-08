# Widowx-arm-control-with-MoveIt
In this tutorial, Moveit will be used to control the widowx arm

# Install dependencies

$ sudo apt install git htop

$ sudo apt install ros-kinetic-moveit ros-kinetic-pcl-ros

# Clone widowx_arm MoveIt repository and build

$ mkdir -p ~/widowx_arm/src

$ cd ~/widowx_arm/src

$ git clone https://github.com/Interbotix/widowx_arm.git

$ git clone https://github.com/Interbotix/arbotix_ros.git -b parallel_gripper

$ cd ~/widowx_arm

$ catkin_make

# ROS control of the arm independent of the SR300 (camera) Sensor

$ cd ~/widowx_arm

$ source devel/setup.bash

$ roslaunch widowx_arm_bringup arm_moveit.launch sim:=false sr300:=false

This should load RVIZ with the proper WidowX arm bringup. You can use "planning" tab to move arm to different poses such as default pose with 0 value for all joints 
, alternate pose or valid random pose. You press update, then plan and execute to let motion planner plan for the path then execute this path.



