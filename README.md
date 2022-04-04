# Widowx-arm-control-with-MoveIt
In this tutorial, Moveit will be used to control the widowx arm. MoveIt is the most widely used software for manipulation and has been used on over 150 robots. By incorporating the latest advances in motion planning, manipulation, 3D perception, kinematics, control and navigation, MoveIt is state of the art software for mobile manipulation.

# Install dependencies

"Htop" is a real-time process monitoring tool for Ubuntu operating system. The htop command is similar to top command, but much improved version.

$ sudo apt install git htop

"pcl-ros" package provides interfaces and tools for bridging a running ROS system to the Point Cloud Library

$ sudo apt install ros-kinetic-moveit ros-kinetic-pcl-ros

If you are using ROS melodic with ubunu 18.04 Run the following command instead

$ sudo apt install ros-melodic-moveit ros-melodic-pcl-ros

# Clone widowx_arm MoveIt repository and build

$ mkdir -p ~/widowx_arm/src

$ cd ~/widowx_arm/src

$ git clone https://github.com/Interbotix/widowx_arm.git

$ git clone https://github.com/Interbotix/arbotix_ros.git -b parallel_gripper

$ cd ~/widowx_arm

$ catkin_make

If you got an error like this 
file:///home/amna/Downloads/catkin_make%20error.png![image](https://user-images.githubusercontent.com/47673149/161577583-2e5546cc-b4b6-4134-97db-8054d84397fa.png)

Go to the following file "widowx_arm/src/widowx_arm/widowx_arm_ikfast_plugin/src/widowx_arm_ikfast_moveit_plugin.cpp" and implement three modifications:

1- replace "boost::shared_ptr<urdf::Joint> joint  " by "urdf::JointConstSharedPtr joint "

2- replace " boost::shared_ptr<urdf::Link> link =" by "urdf::LinkConstSharedPtr link = "

3- replace "boost::const_pointer_cast<urdf::Link>(robot_model.getLink(tip_frame_));" by "urdf::LinkConstSharedPtr(robot_model.getLink(tip_frame_));"

# ROS control of the arm independent of the SR300 (camera) Sensor

Give an access authorization for /dev/ttyUSB0

$ sudo chmod 777 /dev/ttyUSB0

$ cd ~/widowx_arm

$ source devel/setup.bash

$ roslaunch widowx_arm_bringup arm_moveit.launch sim:=false sr300:=false

This should load RVIZ with the proper WidowX arm bringup. You can use "planning" tab to move arm to different poses such as default pose with 0 value for all joints 
, alternate pose or valid random pose. You press update, then plan and execute to let motion planner plan for the path then execute this path.



