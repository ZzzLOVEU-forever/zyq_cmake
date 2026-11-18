cmake_minimum_required(VERSION 3.25)
project(logkeeper VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 1. 包含当前源码目录下的 include 文件夹
include_directories(${PROJECT_SOURCE_DIR}/include)

# 2. 生成 version.h 到 build 目录下
configure_file(
    ${PROJECT_SOURCE_DIR}/include/version.h.in
    ${PROJECT_BINARY_DIR}/version.h
)

# 3. 把 build 目录也加进包含路径，让代码能找到生成的 version.h
include_directories(${PROJECT_BINARY_DIR})

# 4. 直接生成可执行文件
add_executable(logkeeper src/main.cpp src/logkeeper.cpp)

target_compile_options(logkeeper PRIVATE -fexec-charset=GBK)