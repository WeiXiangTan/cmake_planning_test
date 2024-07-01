cmake_minimum_required(VERSION 3.17.0)
project(planning) # 工程名
set(CMAKE_CXX_STANDARD 11)

# ******************* 变量和目录设置 **************************
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) # 动态库和.exe文件都指定到bin目录下
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# ******************* 生成动态库 **************************
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
) # 把所有的.cpp文件生成一个动态库

target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)
# *********************************************************

# ******************* 可执行文件 **************************
add_executable(planning_main planning_main.cpp)

target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# ******************* 链接：让可执行文件链接动态库 **************************
target_link_directories(planning_main
PUBLIC
common
)
