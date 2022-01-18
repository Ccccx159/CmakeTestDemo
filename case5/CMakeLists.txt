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
add_executable(case5 ${srcFiles})
target_link_libraries(case5 ${LIB_M_MATH})

install(TARGETS case5 DESTINATION ${CMAKE_SOURCE_DIR}/release/bin)

# 启用测试
enable_testing()

# 测试程序是否成功运行
add_test(test_run case5 2 10)

# 测试帮助信息是否可以正常提示
add_test(test_usage case5)
set_tests_properties(test_usage PROPERTIES PASS_REGULAR_EXPRESSION "Usage: .* base exponent")

# 测试 5 的平方
add_test(test_5_2 case5 5 2)
set_tests_properties(test_5_2 PROPERTIES PASS_REGULAR_EXPRESSION "is 25")

# 测试 10 的5次方
add_test(test_10_5 case5 10 5)
set_tests_properties(test_10_5 PROPERTIES PASS_REGULAR_EXPRESSION "is 100000")

# 定义一个宏来进行测试
macro(do_test arg1 arg2 result)
  add_test(test_${arg1}_${arg2} case5 ${arg1} ${arg2})
  set_tests_properties(test_${arg1}_${arg2} PROPERTIES PASS_REGULAR_EXPRESSION ${result})
endmacro(do_test)

do_test(3 3 "is 27")
do_test(2 10 "is 1024")
do_test(4 3 "is 64")
