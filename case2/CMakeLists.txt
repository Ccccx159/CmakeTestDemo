# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (case2)

# 指定生成目标
# 1、添加源文件方式
# add_executable(case2 case2.cc mathFunc.cc)

# 2、添加源文件目录方式——aux_source_directory(<dir> <variable>)
# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)
# 关键词 IN, LISTS, STATUS 都需要大写，否则cmake无法识别
foreach(src IN LISTS DIR_SRCS)
  message(STATUS "src files -->:" ${src})
endforeach()

add_executable(case2 ${DIR_SRCS})

