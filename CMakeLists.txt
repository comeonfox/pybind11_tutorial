cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(cmake_example)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(extern/pybind11)
pybind11_add_module(cmake_example src/main.cpp)

target_compile_definitions(cmake_example
                           PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})

find_package(OpenMP)
if(OpenMP_CXX_FOUND)
    target_link_libraries(cmake_example PUBLIC OpenMP::OpenMP_CXX)
endif()

