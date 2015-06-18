cmake_minimum_required(VERSION 2.8.3)
project(path_planning)

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


add_executable(path_planning_Run src/path_planning.cc)
target_link_libraries(path_planning_Run ${GTEST_LIBRARIES} ${catkin_LIBRARIES} pthread)
add_dependencies(path_planning_Run path_planning_path_planning_cc)

catkin_add_gtest(path_planning_utest src/test/utest.cc)
target_link_libraries(path_planning_utest ${catkin_LIBRARIES}) 
