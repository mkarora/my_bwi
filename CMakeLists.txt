cmake_minimum_required(VERSION 2.8.3)
project(my_bwi)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  sensor_msgs
  geometry_msgs
  message_generation
  jaco_msgs
  actionlib
  pcl_ros
  pcl_conversions
  agile_grasp
  tf_conversions
  moveit_ros_planning_interface
  moveit_utils
  moveit_msgs
  segbot_arm_manipulation
  segbot_arm_perception
)

find_package(PCL 1.7 REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

catkin_package(
  DEPENDS segbot_arm_perception
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(pour_demo src/pour_demo.cpp)
target_link_libraries(pour_demo ${catkin_LIBRARIES} )
add_dependencies(pour_demo jaco_msgs_gencpp pour_gencpp)
