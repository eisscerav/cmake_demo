cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(recipe-02 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(CURL REQUIRED)

message(STATUS ${CURL_FOUND})
message(STATUS ${CURL_INCLUDE_DIR})
message(STATUS ${CURL_LIBRARY})

add_executable(main main.cc)

target_include_directories(main
  PRIVATE
  ${CURL_INCLUDE_DIR}
)

target_link_libraries(main
  PRIVATE
  ${CURL_LIBRARY}
)
