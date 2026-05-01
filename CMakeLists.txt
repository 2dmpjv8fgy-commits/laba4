cmake_minimum_required(VERSION 3.10)
project(print)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library(print STATIC sources/print.cpp)

add_executable(example1 examples/example1.cpp)
target_link_libraries(example1 print)
