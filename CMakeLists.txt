cmake_minimum_required(VERSION 3.3)
project(nek-cpp)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES
    nek.cpp)

add_executable(nek-cpp ${SOURCE_FILES})

set(EXECUTABLE_OUTPUT_PATH dist/${CMAKE_BUILD_TYPE})

