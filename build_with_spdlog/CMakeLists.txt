cmake_minimum_required(VERSION 3.11 FATAL_ERROR)

# project name and language
project(ext_spdlog LANGUAGES CXX)

# require C++11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(spdlog_demo main.cc)

message(STATUS ${CMAKE_CURRENT_SOURCE_DIR})

#target_include_directories(spdlog_demo PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/spd/include/)
# 指定lib文件路径
#target_link_libraries(	spdlog_demo PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/lib)

include(FetchContent)     

FetchContent_Declare(	spdlog	#
   					GIT_REPOSITORY https://github.com/gabime/spdlog.git
   					GIT_TAG v1.x # 
   					SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/spdlog # 
   					)

FetchContent_GetProperties(spdlog)

message(STATUS "spdlog_POPULATED ${spdlog_POPULATED}")
message(STATUS "spdlog_SOURCE_DIR ${spdlog_SOURCE_DIR}")
message(STATUS "spdlog_BINARY_DIR ${spdlog_BINARY_DIR}")

if(NOT spdlog_POPULATED)
  FetchContent_Populate(spdlog)
  message(STATUS "spdlog_SOURCE_DIR:${spdlog_SOURCE_DIR} spdlog_BINARY_DIR:${spdlog_BINARY_DIR}")
  add_subdirectory(${spdlog_SOURCE_DIR} ${spdlog_BINARY_DIR})
endif()

message(STATUS "spdlog_POPULATED ${spdlog_POPULATED}")
message(STATUS "spdlog_SOURCE_DIR ${spdlog_SOURCE_DIR}")
message(STATUS "spdlog_BINARY_DIR ${spdlog_BINARY_DIR}")
#FetchContent_MakeAvailable(spdlog)

# 项目中使用spdlog
#target_link_libraries(spdlog_demo PRIVATE spdlog::spdlog)
target_link_libraries(spdlog_demo PRIVATE spdlog)

