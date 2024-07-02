cmake_minimum_required(VERSION 3.17.0)
project(planning) 
set(CMAKE_CXX_STANDARD 11)

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

add_library(common SHARED ${SRC_LISTS}) 
target_include_directories(common PUBLIC ${PROJECT_SOURCE_DIR}/include) 

add_executable(planning_main planning_main.cpp ${SRC_LISTS})
target_include_directories(planning_main PUBLIC ${PROJECT_SOURCE_DIR}/include)

target_link_directories(planning_main PUBLIC common)
