cmake_minimum_required(VERSION 3.14)


set(CMAKE_CXX_STANDARD 17)
include("tools/gate/cmake/HunterGate.cmake")
HunterGate(
        URL "https://github.com/cpp-pm/hunter/archive/v0.23.218.tar.gz"
        SHA1 "9a3594a61227967fb92159339ba326701b287b19"
)
project(hunterproject)
hunter_add_package(Boost
        COMPONENTS
        program_options
        thread
        log
        filesystem)
find_package(Boost CONFIG REQUIRED COMPONENTS
        program_options
        thread
        log
        log_setup
        filesystem)
hunter_add_package(rocksdb)
find_package(RocksDB CONFIG REQUIRED)
add_executable(hunterproject main.cpp)
#target_include_directories(hunterproject  INTERFACE $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)
target_link_libraries(hunterproject pthread Boost::log Boost::thread Boost::program_options Boost::log_setup Boost::filesystem
        RocksDB::rocksdb pthread)
