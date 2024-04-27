cmake_minimum_required(VERSION 3.5)
project(kdl_tutorial_01)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(orocos_kdl_vendor REQUIRED)
find_package(kdl_parser REQUIRED)

set(dependencies
  rclcpp
  std_msgs
  orocos_kdl_vendor
  kdl_parser
)

#########
# build #
#########
add_executable(main
  src/main.cpp
)
target_include_directories(main PRIVATE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>)
ament_target_dependencies(main ${dependencies})

###########
# install #
###########
install(TARGETS
  main
  DESTINATION lib/${PROJECT_NAME}
)

install(
  DIRECTORY
    launch
    urdf
  DESTINATION share/${PROJECT_NAME}
)

ament_package()
