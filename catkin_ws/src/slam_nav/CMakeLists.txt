cmake_minimum_required(VERSION 3.0.2)
project(slam_nav)

find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs nav_msgs geometry_msgs sensor_msgs)

catkin_package()

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch)

install(DIRECTORY config/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config)

install(DIRECTORY scripts/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/scripts)
