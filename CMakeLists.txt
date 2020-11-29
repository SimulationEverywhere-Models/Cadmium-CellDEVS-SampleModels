cmake_minimum_required (VERSION 3.6.1)
project(celldevs-tutorial)

set (CMAKE_CXX_STANDARD 17)
set (CMAKE_CXX_COMPILER "g++")
add_compile_options(-g)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../../cadmium/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../../cadmium/json/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../../DESTimes/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

set(Boost_USE_MULTITHREADED TRUE)
find_package(Boost COMPONENTS unit_test_framework system thread REQUIRED)

file(MAKE_DIRECTORY logs)

add_executable(1_1_spatial_sir 1_1_spatial_sir/main.cpp)
add_executable(1_2_spatial_sir_config 1_2_spatial_sir_config/main.cpp)
add_executable(1_3_spatial_sird 1_3_spatial_sird/main.cpp)
add_executable(1_4_spatial_sirds 1_4_spatial_sirds/main.cpp)

add_executable(2_1_agent_sir 2_1_agent_sir/main.cpp)
add_executable(2_2_agent_sir_config 2_2_agent_sir_config/main.cpp)
add_executable(2_3_agent_sird 2_3_agent_sird/main.cpp)
add_executable(2_4_agent_sirds 2_4_agent_sirds/main.cpp)

target_link_libraries(1_1_spatial_sir PUBLIC ${Boost_LIBRARIES})
target_link_libraries(1_2_spatial_sir_config  PUBLIC ${Boost_LIBRARIES})
target_link_libraries(1_3_spatial_sird  PUBLIC ${Boost_LIBRARIES})
target_link_libraries(1_4_spatial_sirds  PUBLIC ${Boost_LIBRARIES})

target_link_libraries(2_1_agent_sir  PUBLIC ${Boost_LIBRARIES})
target_link_libraries(2_2_agent_sir_config  PUBLIC ${Boost_LIBRARIES})
target_link_libraries(2_3_agent_sird  PUBLIC ${Boost_LIBRARIES})
target_link_libraries(2_4_agent_sirds  PUBLIC ${Boost_LIBRARIES})
