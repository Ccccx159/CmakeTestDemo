# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (case3_1_withSourceFile)

# 添加子目录
add_subdirectory(${CMAKE_SOURCE_DIR}/math)
list(APPEND srcFile ${subDirFile})
# 添加当前目录源文件
aux_source_directory(${CMAKE_SOURCE_DIR} CurrentSrcs)
list(APPEND srcFile ${CurrentSrcs})

foreach(file IN LISTS srcFile)
  message(STATUS "src file is-->:" ${file})
endforeach()

# 添加可执行文件
add_executable(case3_1 ${srcFile})

