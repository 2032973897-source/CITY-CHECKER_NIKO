cmake_minimum_required(VERSION 3.0.2)
project(vision)

find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs sensor_msgs image_transport cv_bridge message_generation)

add_message_files(FILES Detection.msg Detections.msg)

generate_messages(DEPENDENCIES std_msgs sensor_msgs)

catkin_package(CATKIN_DEPENDS roscpp rospy std_msgs sensor_msgs image_transport cv_bridge message_runtime)

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch)

install(DIRECTORY config/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config)

install(DIRECTORY scripts/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/scripts)

install(DIRECTORY models/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/models)
