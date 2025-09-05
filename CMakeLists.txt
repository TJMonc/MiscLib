cmake_minimum_required(VERSION 3.21)
add_definitions(-std=c++20)
project(Misc)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${FETCHCONTENT_BASE_DIR}/lib)
#set source dir fo library

#define target
file(GLOB SOURCES "src/*.cpp")
add_library(${PROJECT_NAME} SHARED ${SOURCES})



#set variables
set(SFML_SRC_DIR ${FETCHCONTENT_BASE_DIR}/sfml-src)
set(SFML_BUILD_DIR ${FETCHCONTENT_BASE_DIR}/lib)
set(INCLUDE_DIRECTORIES ${SFML_SRC_DIR}/include "include")
set(LINK_DIRECTORIES ${SFML_BUILD_DIR})
set(LINK_LIBRARIES libsfml-graphics.a libsfml-window.a libsfml-audio.a libsfml-main.a libsfml-network.a libsfml-system.a)

#configure target
option(BUILD_SHARED_LIBS "Build shared libraries" ON)
target_include_directories(${PROJECT_NAME} PRIVATE ${INCLUDE_DIRECTORIES})
target_link_directories(${PROJECT_NAME} PRIVATE ${LINK_DIRECTORIES})
target_link_libraries(${PROJECT_NAME} ${LINK_LIBRARIES})


