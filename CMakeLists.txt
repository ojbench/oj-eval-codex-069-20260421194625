cmake_minimum_required(VERSION 3.10)
project(oj069)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# main binary required by OJ git compilation process
add_executable(code src/main.cpp)
target_include_directories(code PRIVATE ${CMAKE_SOURCE_DIR})

# local tests target (not required by OJ)
add_executable(unit_tests tests/test.cpp)
target_include_directories(unit_tests PRIVATE ${CMAKE_SOURCE_DIR})
if (MSVC)
  target_compile_options(unit_tests PRIVATE /W4)
else()
  target_compile_options(unit_tests PRIVATE -Wall -Wextra -Wpedantic)
endif()
