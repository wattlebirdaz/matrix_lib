cmake_minimum_required(VERSION 3.7)

project(matrix_lib
    VERSION 1.0.0
    DESCRIPTION "Matrix Library"
    LANGUAGES CXX)

enable_testing()


add_library(matrix STATIC ./src/matrix.cpp)
target_compile_features(matrix PRIVATE cxx_std_11)
target_include_directories(matrix PUBLIC ./include)
set_target_properties(matrix
    PROPERTIES
    VERSION ${PROJECT_VERSION})


add_subdirectory(test)
add_test(test01 test/test01)
