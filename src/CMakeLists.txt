cmake_minimum_required(VERSION 3.7)

project(matrix_lib_src)

add_library(matrix STATIC ./matrix.cpp)
target_compile_features(matrix PRIVATE cxx_std_11)
target_include_directories(matrix PUBLIC ../include)
