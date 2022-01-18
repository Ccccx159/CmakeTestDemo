# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

set(lib_math ${CMAKE_CURRENT_SOURCE_DIR} CACHE STRING "")
message(STATUS "lib_math-->:" ${lib_math})
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} libSrc)

add_library(mathFunc ${libSrc})
