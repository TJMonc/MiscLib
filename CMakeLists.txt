cmake_minimum_required(VERSION 3.21)
add_definitions(-std=c++20)
project(Misc)

#set source dir fo library
set(MISCLIB_DIR ${CMAKE_SOURCE_DIR})

#define target
file(GLOB SOURCES "src/*.cpp")
add_library(${PROJECT_NAME} SHARED ${SOURCES})



#set variables
set(SFML_SRC_DIR ${FETCHCONTENT_BASE_DIR}/sfml-src)
set(SFML_BUILD_DIR ${FETCHCONTENT_BASE_DIR}/sfml-build)
set(INCLUDE_DIRECTORIES ${SFML_SRC_DIR}/include "include")
set(LINK_DIRECTORIES ${SFML_BUILD_DIR}/lib)
set(LINK_LIBRARIES libsfml-graphics.a libsfml-window.a libsfml-audio.a libsfml-main.a libsfml-network.a libsfml-system.a)

#configure target
option(BUILD_SHARED_LIBS "Build shared libraries" ON)
set_target_properties(Misc PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin
    LIBRARY_OUTPUT_DIRECTORY ${MISCLIB_DIR}/lib
)
target_include_directories(${PROJECT_NAME} PRIVATE ${INCLUDE_DIRECTORIES})
target_link_directories(${PROJECT_NAME} PRIVATE ${LINK_DIRECTORIES})
target_link_libraries(${PROJECT_NAME} ${LINK_LIBRARIES})


