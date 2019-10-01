cmake_minimum_required(VERSION 2.8)
project(7zpp)
include(CTest)

file(GLOB 7ZPP_SOURCES  ${PROJECT_SOURCE_DIR}/7zpp/*.cpp )
add_library(7zpp ${7ZPP_SOURCES})
target_include_directories(7zpp PRIVATE  ${PROJECT_SOURCE_DIR}   ${PROJECT_SOURCE_DIR}/7zpp ${PROJECT_SOURCE_DIR}/7z/C  ${PROJECT_SOURCE_DIR}/7z/CPP)

set(Boost_USE_STATIC_LIBS ON) 
set(Boost_USE_MULTITHREADED ON)  
find_package(Boost COMPONENTS filesystem ) 
# Setup testing
IF( NOT CMAKE_BUILD_TYPE )
   SET( CMAKE_BUILD_TYPE Debug)
ENDIF()

#The following is needed to run tests properly
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/build)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY $${CMAKE_SOURCE_DIR}/build)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/build)
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/build)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/build)
