cmake_minimum_required(VERSION 3.12)

project(billboard_top100 
        VERSION 0.0.1
        LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)

file(GLOB HEADERS CONFIGURE_DEPENDS "${billboard_top100_SOURCE_DIR}/src/*.hpp")
file(GLOB SOURCES CONFIGURE_DEPENDS "${billboard_top100_SOURCE_DIR}/src/*.cpp")

add_library(treeLib ${SOURCES} ${HEADERS})

target_include_directories(treeLib PUBLIC src)

add_executable(main app/main.cpp)

add_subdirectory(dependencies)
target_link_libraries(treeLib PRIVATE csv)
target_link_libraries(main PRIVATE treeLib)
