cmake_minimum_required(VERSION 3.0)
project(nearlab_msgs)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11 -g -Wall)

find_package(catkin REQUIRED COMPONENTS
  std_msgs
  roscpp
  message_generation
)

add_message_files(DIRECTORY ${PROJECT_SOURCE_DIR}/msg FILES
  ControlStamped.msg
)

add_service_files(DIRECTORY srv FILES
  energy_optimal_traj.srv
  attitude_traj.srv
)

generate_messages(DEPENDENCIES
  std_msgs
)

catkin_package(CATKIN_DEPENDS
  std_msgs
  roscpp
  message_runtime
)

#execute_process(
#  COMMAND "cp " ${PROJECT_SOURCE_DIR}"/third_party/libPxLApi.so /usr/lib/libPxLApi.so"}
#)

#########
# BUILD #
#########
include_directories(
  ${catkin_INCLUDE_DIRS}
)
#install(DIRECTORY launch/
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
#  PATTERN ".svn" EXCLUDE
#)
