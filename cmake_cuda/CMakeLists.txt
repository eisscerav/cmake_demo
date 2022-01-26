cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
project(cmake_and_cuda)
enable_language(CUDA)

add_executable(main main.cpp)
add_subdirectory(kernels)
target_link_libraries(main kernels)

