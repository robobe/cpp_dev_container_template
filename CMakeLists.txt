cmake_minimum_required(VERSION 3.10)
project(cpp_dev_container_template)

enable_testing()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(src)
add_subdirectory(helper)
add_subdirectory(tests)