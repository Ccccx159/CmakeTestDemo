# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

configure_file("${PROJECT_SOURCE_DIR}/inc/config.h.in" "${PROJECT_SOURCE_DIR}/inc/config.h")
include_directories("${PROJECT_SOURCE_DIR}/inc")
option(USE_M_MATH "Use provided math implementation" ON)

if (USE_M_MATH)
  add_subdirectory(${CMAKE_SOURCE_DIR}/lib/math)
  include_directories("${lib_math_path}")
  set(LIB_M_MATH ${lib_math} CACHE STRING "")
endif(USE_M_MATH)

add_subdirectory(${CMAKE_SOURCE_DIR}/src)
add_executable(case4 ${srcFiles})
target_link_libraries(case4 ${LIB_M_MATH})

