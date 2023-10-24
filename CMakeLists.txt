cmake_minimum_required(VERSION 3.10)

# Set the project name
project(Physac)

# Specify the C standard
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED True)

# Include directories
include_directories(${CMAKE_SOURCE_DIR}/src)

# Find raylib
# https://github.com/raysan5/raylib/wiki/Working-on-GNU-Linux
find_package(raylib 3.0 REQUIRED)

# Compile the example files
file(GLOB EXAMPLE_SOURCES examples/*.c)
foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    # Extract the filename without the extension
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    
    # Create an executable for each example
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})

    target_link_libraries(${EXAMPLE_NAME} raylib m) 
endforeach()
