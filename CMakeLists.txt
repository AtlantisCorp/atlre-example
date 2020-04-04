# This CMakeLists actually compiles the AtlRE example project, and links it
# against the AtlRE shared library.

cmake_minimum_required(VERSION 3.0)

# All Atl's projects  must be at least compiled for C++17.
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# This is our example project. You can rename it as you want.
project(atlreExample VERSION 1.0)

# This is our example executable. Rename it as you want.
add_executable(example)

# Our sources should be localized under the 'src' directory.
file(GLOB HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h")
file(GLOB SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
target_sources(example PRIVATE ${HEADERS} ${SOURCES})

# Now adds the AtlRE library.
add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/libs/atlre")
target_include_directories(example PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/libs/atlre/includes")
target_link_directories(example PRIVATE atl)
