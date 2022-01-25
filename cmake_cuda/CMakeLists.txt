cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
project(cmake_and_cuda)
enable_language(CUDA)

add_executable(main main.cpp)
add_subdirectory(kernels)

# set_property(TARGET main 
#              PROPERTY CUDA_SEPARABLE_COMPILATION ON)
target_link_libraries(main kernels)

enable_language(CUDA)
add_library(kernels
test.cu
test.cuh
)
target_compile_features(kernels PUBLIC cxx_std_11)
set_target_properties(kernels
                       PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
target_link_libraries(kernels)
