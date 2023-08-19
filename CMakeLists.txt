set(CMAKE_GENERATOR, "mingw32-make")
cmake_minimum_required(VERSION 3.22.5)
set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")

project (pixel_browser)

file(GLOB SOURCES src/*.c)
file(GLOB_RECURSE HEADERS src/lexbor-2.2.0/source/lexbor/*.h)

add_executable(pixel_browser ${SOURCES})

target_include_directories(pixel_browser
    PRIVATE 
        ${HEADERS}
        ${PROJECT_SOURCE_DIR}/src/include
)
target_link_libraries(pixel_browser
    PRIVATE 
        mingw32
        ${CMAKE_SOURCE_DIR}/src/lexbor-2.2.0/liblexbor.dll.a
        ${CMAKE_SOURCE_DIR}/src/lexbor-2.2.0/liblexbor.dll
)