cmake_minimum_required(VERSION 3.10)

# Project name
project(manip-histogram VERSION 1.0)

# Specifying the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Adding the executable to be created. This needs to come before trying to compile it with commands as: target_include_directories.
add_executable(histogram src/histogram.cpp)
add_executable(equalize src/equalize.cpp)
add_executable(motion-detector src/motiondetector.cpp)

# Finds and loads the settings from the OPENCV package
find_package(OpenCV REQUIRED)

# Add header file directories to the project
include_directories(${OpenCV_INCLUDE_DIRS})
include_directories("${PROJECT_BINARY_DIR}")
#target_include_directories(pixel-manip PUBLIC
#							"${PROJECT_BINARY_DIR}")

# Linking the created executable to the OpenCV libraries.
target_link_libraries(histogram ${OpenCV_LIBRARIES})
target_link_libraries(equalize ${OpenCV_LIBRARIES})
target_link_libraries(motion-detector ${OpenCV_LIBRARIES})
# Exporting the compile_commands.json so we can use eglot
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
