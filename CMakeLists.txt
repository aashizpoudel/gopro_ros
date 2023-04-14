cmake_minimum_required(VERSION 2.8.3)
project(gopro_ros)

find_package(catkin REQUIRED COMPONENTS
  rospy
  std_msgs
  geometry_msgs
  tf
  tf2
  actionlib
  actionlib_msgs
)

# add_action_files(
#   DIRECTORY action
#   FILES GoToPose.action
# )

if (CATKIN_ENABLE_TESTING)
  catkin_add_nosetests(tests)
endif()

if (CATKIN_ENABLE_TESTING)
  find_package(rostest REQUIRED)
#  add_rostest(tests/your_first_rostest.test)
#  add_rostest(tests/your_second_rostest.test)
endif()



catkin_python_setup()

generate_messages (
  DEPENDENCIES actionlib_msgs std_msgs geometry_msgs
)


catkin_package(
  CATKIN_DEPENDS actionlib_msgs
)

catkin_install_python(PROGRAMS nodes/gopro_camera nodes/udp_stream
   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})





