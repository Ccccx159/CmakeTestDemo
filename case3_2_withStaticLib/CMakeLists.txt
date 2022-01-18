# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

message(STATUS "PROJECT_SOURCE_DIR is-->:" ${PROJECT_SOURCE_DIR})
message(STATUS "CMAKE_SOURCE_DIR is-->:" ${CMAKE_SOURCE_DIR})
message(STATUS "PROJECT_BINARY_DIR is-->:" ${PROJECT_BINARY_DIR})
message(STATUS "CMAKE_BINARY_DIR is-->:" ${CMAKE_BINARY_DIR})
add_subdirectory(${CMAKE_SOURCE_DIR}/lib/math)
add_subdirectory(${CMAKE_SOURCE_DIR}/src)

include_directories(${lib_math})

list(APPEND projFiles ${srcFiles})

foreach(src IN LISTS projFiles)
  message(STATUS "src is-->:" ${src})
endforeach()

add_executable(case3_2 ${projFiles})

target_link_libraries(case3_2 mathFunc)