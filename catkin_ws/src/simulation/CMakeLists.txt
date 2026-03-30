cmake_minimum_required(VERSION 3.0.2)
project(simulation)

find_package(catkin REQUIRED)

catkin_package()

install(DIRECTORY gazebo/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/gazebo)

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch)

install(DIRECTORY config/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config)

install(DIRECTORY scripts/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/scripts)
