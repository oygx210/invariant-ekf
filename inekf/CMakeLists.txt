cmake_minimum_required(VERSION 3.10)
project(modrob CXX)

include(CMakeHeader.cmake)

# ##############################################################################
# IEKF
add_library(iekf SHARED src/IEKF.cpp)
target_link_libraries(iekf utils)
target_add_test_case(test_iekf test_iekf.cpp)
target_link_libraries(test_iekf iekf)
# ##############################################################################

# ##############################################################################
# DataLoader
add_library(DataLoader SHARED src/DataLoader.cpp)
add_executable(iekf_example src/iekf_example.cpp)
target_link_libraries(iekf_example DataLoader iekf)
# ##############################################################################

# ##############################################################################
# utils
add_library(utils SHARED src/utils.cpp)
target_add_test_case(test_utils test_utils.cpp)
target_link_libraries(test_utils utils)
# ##############################################################################
