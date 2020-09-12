cmake_minimum_required(VERSION 3.7)

project(matrix_lib_test)

find_package(Threads)
add_executable(test01 test.cpp)
target_link_libraries(test01 matrix)
target_link_libraries(test01 ${CMAKE_THREAD_LIBS_INIT})
target_link_libraries(test01 gtest_main)
target_link_libraries(test01 gtest)

