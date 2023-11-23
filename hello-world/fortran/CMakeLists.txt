cmake_minimum_required(VERSION 3.10)

project(SimpleFortranProject LANGUAGES Fortran)

# Specify the Fortran source file
add_executable(fortran_hello main.f90)

# Optionally, specify the Fortran compiler (uncomment the line below to manually set a compiler)
# set(CMAKE_Fortran_COMPILER "/path/to/your/fortran/compiler")

