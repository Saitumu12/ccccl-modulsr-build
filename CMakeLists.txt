cmake_minimum_required(VERSION 3.25)

project(CCCL VERSION 2.1.0 LANGUAGES CXX CUDA)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CUDA_STANDARD 17)
set(CMAKE_CUDA_STANDARD_REQUIRED ON)

# Compile for all GPU generations: 70=V100 80=A100 86=RTX3090 89=RTX4090 90=H100
set(CMAKE_CUDA_ARCHITECTURES 70 80 86 89 90)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# ORDER MATTERS — libcudacxx first (no deps), CUB second, Thrust third
add_subdirectory(libcudacxx)
add_subdirectory(cub)
add_subdirectory(thrust)
add_subdirectory(tests)
add_subdirectory(examples)
