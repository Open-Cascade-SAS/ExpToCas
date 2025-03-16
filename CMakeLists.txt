# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
cmake_minimum_required (VERSION 3.8)

project ("ExpToCas")

include("${CMAKE_CURRENT_SOURCE_DIR}/adm/cmake/FindOCCT.cmake")

# Include sub-projects.
add_subdirectory ("src")

set(CMAKE_CXX_STANDARD 17) # Enable c++17 standard
