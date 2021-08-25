cmake_minimum_required(VERSION 3.18)
project(libg719_decode)

file(GLOB_RECURSE SOURCES "reference_code/*.c")

add_library(g719_decode STATIC g719.c ${SOURCES})

target_include_directories(g719_decode PRIVATE reference_code/include)

set_property(TARGET g719_decode PROPERTY POSITION_INDEPENDENT_CODE ON)
target_compile_definitions(g719_decode PRIVATE VAR_ARRAYS)

set(CMAKE_INSTALL_PREFIX ${CMAKE_CURRENT_BINARY_DIR})
install(TARGETS g719_decode DESTINATION ${CMAKE_INSTALL_PREFIX})
