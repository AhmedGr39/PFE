cmake_minimum_required(VERSION 3.0.2)
project(pfe)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  message_generation
  rosserial_python
  rospy
  roscpp
  std_msgs
)


catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES pfe
  CATKIN_DEPENDS message_generation roscpp std_msgs rosserial_python
#  DEPENDS system_lib
)

add_message_files(
  FILES
  Encoder.msg  # <-- add your custom message file name here
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)


## Install launch file
install(FILES launch/ros_serial.launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)

