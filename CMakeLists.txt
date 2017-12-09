cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 11)

include(cmake/HunterGate.cmake)

HunterGate(
    URL "https://github.com/ZolbergN/hunter/archive/v0.19.137.1.tar.gz"
    SHA1 "f810eb33eb64a6d35d12bb73ea843bc4ef0e24ed"
)

project(main)
hunter_add_package(CURL)
find_package(CURL CONFIG REQUIRED)

hunter_add_package(OpenSSL)
find_package(OpenSSL REQUIRED)

add_executable(main ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp)
target_link_libraries(main PRIVATE CURL::libcurl OpenSSL::SSL OpenSSL::Crypto)
