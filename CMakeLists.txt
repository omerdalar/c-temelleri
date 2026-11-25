cmake_minimum_required(VERSION 3.20)
project(c_temelleri C)

# C11 standard, same as: gcc -std=c11
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Strict warnings, same as: gcc -Wall -Wextra -Werror
add_compile_options(-Wall -Wextra -Werror)

# One executable per lesson folder
add_executable(01-hello 01-hello/hello.c)
