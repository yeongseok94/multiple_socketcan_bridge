cmake_minimum_required(VERSION 3.0.2)
project(multiple_socketcan_bridge)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_CXX_STANDARD 14)
endif()

find_package(catkin REQUIRED
  COMPONENTS
    can_msgs
    rosconsole_bridge
    roscpp
    socketcan_interface
)

catkin_package(
  INCLUDE_DIRS
    include
  LIBRARIES
    socketcan_to_topic
    topic_to_socketcan
  CATKIN_DEPENDS
    can_msgs
    rosconsole_bridge
    roscpp
    socketcan_interface
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

# multiple_socketcan_bridge_node
add_executable(${PROJECT_NAME}_node
  src/${PROJECT_NAME}_node.cpp
)
target_link_libraries(${PROJECT_NAME}_node
  topic_to_socketcan
  socketcan_to_topic
  ${catkin_LIBRARIES}
)

