cmake_minimum_required(VERSION 3.3)
project(nek-cpp)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(ENV{LLVM_DIR} /usr/local/Cellar/llvm/3.6.2/)

find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

set(SOURCE_FILES
    nek.cpp)

add_executable(nek-cpp ${SOURCE_FILES})

set(EXECUTABLE_OUTPUT_PATH dist/${CMAKE_BUILD_TYPE})

# Find the libraries that correspond to the LLVM components
# that we wish to use
llvm_map_components_to_libnames(llvm_libs support core irreader)

# Link against LLVM libraries
target_link_libraries(nek-cpp ${llvm_libs})