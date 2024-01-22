# Set CMake minimum version to currently using
cmake_minimum_required( VERSION 3.26 )

# Setup Project name
message( "Configuring project: CatchBench" )
project( CatchBench
         VERSION 0.0.1
         LANGUAGES CXX )

# Set C++ Standard to C++20
set( CMAKE_CXX_STANDARD 20 )

# Use solution folders
set_property( GLOBAL PROPERTY USE_FOLDERS ON )

# Force CMake Install directory into build folder
set( CMAKE_DEBUG_POSTFIX d CACHE STRING "" FORCE )
set( CMAKE_CURRENT_BINARY_DIR ${CMAKE_CURRENT_SOURCE_DIR}/build/vc16_x64 CACHE PATH "" FORCE )
set( CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_BINARY_DIR}/install CACHE PATH "" FORCE )

# Set CMake Module Path
set( CMAKE_MODULE_PATH
     ${CMAKE_CURRENT_SOURCE_DIR}/cmake
     CACHE PATH "" FORCE )

include( FetchContent )

# Fetch Catch2
FetchContent_Declare( Catch2
                      GIT_REPOSITORY https://github.com/catchorg/Catch2
                      GIT_TAG 05e10df )
FetchContent_MakeAvailable( Catch2 )

# Fetch Benchmark
FetchContent_Declare( GoogleTest
                      GIT_REPOSITORY https://github.com/google/googletest
                      GIT_TAG f8d7d77 )
FetchContent_Declare( Benchmark
                      GIT_REPOSITORY  https://github.com/google/benchmark
                      GIT_TAG 3441176 )
FetchContent_MakeAvailable( GoogleTest Benchmark )

# Add some demo code to test functionality
#TODO
