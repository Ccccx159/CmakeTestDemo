# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} curFiles)

set(srcFiles ${curFiles} CACHE STRING "")
