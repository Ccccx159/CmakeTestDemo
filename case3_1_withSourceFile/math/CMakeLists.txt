# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 通过list(APPEND <variable> ...)将子目录文件导入到变量中，通过变量传递给外层cmake
set(subDir ${CMAKE_SOURCE_DIR}/math CACHE STRING "")
message(STATUS "subDir is -->:" ${subDir})
aux_source_directory(${subDir} subDirFile_math)

# 通过 set 一个 CACHE 变量，来实现变量的传递
set(subDirFile ${subDirFile_math} CACHE STRING "")