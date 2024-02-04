cmake_minimum_required(VERSION 3.28)
project(SC1007_LL C)

set(CMAKE_C_STANDARD 11)
find_package(check)

enable_testing()

foreach (X RANGE 1 4)
    add_subdirectory(src/q${X})
endforeach ()