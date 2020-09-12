cmake_minimum_required(VERSION 3.7)

project(matrix_lib
    VERSION 1.0.0
    DESCRIPTION "Matrix Library"
    LANGUAGES CXX)

enable_testing()

add_subdirectory(src)
add_subdirectory(test)
add_test(test01 test/test01)
