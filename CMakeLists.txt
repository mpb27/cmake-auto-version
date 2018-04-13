cmake_minimum_required(VERSION 3.10)
project(auto_build_increment)

set(CMAKE_CXX_STANDARD 11)

add_executable(test_increment main.cpp version.h)

ADD_CUSTOM_TARGET(
        auto_increment_version
        ${CMAKE_COMMAND}
        -D VERSION_FILE=${CMAKE_SOURCE_DIR}/version.h
        -P ${CMAKE_SOURCE_DIR}/AutoVersion.cmake
)
ADD_DEPENDENCIES(test_increment auto_increment_version)
