cmake_minimum_required(VERSION 2.8.3)
project(rtimulib_ros)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
)

catkin_package(
    LIBRARIES rtimulib_ros
    CATKIN_DEPENDS roscpp sensor_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(rtimulib_ros src/rtimulib_ros.cpp)

target_link_libraries(rtimulib_ros
  ${catkin_LIBRARIES}
  RTIMULib
)

#Add all files in subdirectories of the project in
# a dummy_target so qtcreator have access to all files
FILE(GLOB_RECURSE extra_files
    ${CMAKE_SOURCE_DIR}/*)
add_custom_target(dummy_${PROJECT_NAME} SOURCES ${extra_files})
