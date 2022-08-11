cmake_minimum_required(VERSION 3.0.2)
project(pluginlib_calculator)

## Find catkin dependencies
find_package(catkin REQUIRED COMPONENTS pluginlib roscpp)

## Find Boost (headers only)
find_package(Boost REQUIRED)

## Define catkin exports
catkin_package(
  INCLUDE_DIRS include
  LIBRARIES pluginlib_calculator
  CATKIN_DEPENDS pluginlib roscpp
  DEPENDS Boost
)

include_directories(include ${catkin_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

## pluginlib_tutorials library
add_library(pluginlib_calculator src/calculator_plugins.cpp)
target_link_libraries(pluginlib_calculator ${catkin_LIBRARIES})

## polygon_loader executable
add_executable(calculator_loader src/calculator_loader.cpp)
target_link_libraries(calculator_loader ${catkin_LIBRARIES})