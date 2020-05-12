cmake_minimum_required(VERSION 3.14)
project(hunterproject)

set(CMAKE_CXX_STANDARD 17)
HunterGate(
        URL "https://github.com/cpp-pm/hunter/archive/v0.23.218.tar.gz"
        SHA1 "9a3594a61227967fb92159339ba326701b287b19"
)
hunter_add_package(GTest)
find_package(GTest CONFIG REQUIRED)
add_executable(hunterproject main.cpp)