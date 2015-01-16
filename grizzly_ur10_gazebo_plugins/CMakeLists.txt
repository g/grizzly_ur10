cmake_minimum_required(VERSION 2.8.3)
project(grizzly_ur10_gazebo_plugins)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS std_msgs gazebo_plugins actionlib tf image_transport control_msgs trajectory_msgs geometry_msgs sensor_msgs roscpp message_generation gazebo_ros)

find_package(gazebo REQUIRED)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)
include_directories(
  ${PROJECT_SOURCE_DIR}/include
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

add_message_files(
    FILES
    SModelRobotInput.msg 
    SModelRobotOutput.msg
) 

generate_messages(
    DEPENDENCIES
    std_msgs
)

catkin_package(
   DEPENDS gazebo_plugins gazebo_ros roscpp
)



add_library(RobotiqHandPlugin src/RobotiqHandPlugin.cpp)
set_target_properties(RobotiqHandPlugin PROPERTIES LINK_FLAGS "${ld_flags}")
set_target_properties(RobotiqHandPlugin PROPERTIES COMPILE_FLAGS "${cxx_flags}")
target_link_libraries(RobotiqHandPlugin ${catkin_LIBRARIES})
add_dependencies(RobotiqHandPlugin grizzly_ur10_gazebo_plugins_gencpp ${CATKIN_EXPORTED_TARGETS} grizzly_ur10_gazebo_EXPORTED_TARGETS)


install(TARGETS RobotiqHandPlugin DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}/${PROJECT_NAME}/plugins/)

install(DIRECTORY msg/ include/ DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})
