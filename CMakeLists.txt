cmake_minimum_required(VERSION 2.8.3)
project(PathPlanning)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
)

find_package(GTest REQUIRED)

catkin_package(
  DEPENDS system_lib
    CATKIN_DEPENDS message_runtime
)

include_directories(
  include/${PROJECT_NAME}
  ${catkin_INCLUDE_DIRS}
  ${GTEST_INCLUDE_DIRS}
)


add_executable(PathPlanning_Run src/PathPlanning.cpp)
target_link_libraries(PathPlanning_Run ${GTEST_LIBRARIES} ${catkin_LIBRARIES} pthread)
add_dependencies(PathPlanning_Run PathPlanning_pathplanning_cpp)

catkin_add_gtest(PathPlanning_utest src/test/utest.cpp)
target_link_libraries(PathPlanning_utest ${catkin_LIBRARIES}) 
