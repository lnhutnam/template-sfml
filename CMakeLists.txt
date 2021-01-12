cmake_minimum_required(VERSION 3.17)
# Set project name
set(PROJECT_NAME "test_sfml")
project(${PROJECT_NAME})

# config linker static
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static")
set(SFML_STATIC_LIBRARIES TRUE)
set(SFML_DIR "${CMAKE_CURRENT_LIST_DIR}/libs/SFML/lib/cmake/SFML")
file(COPY libs/SFML/bin/openal32.dll DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

# config cpp standard 17
set(CMAKE_CXX_STANDARD 17)
# link the filesystem
link_libraries(stdc++fs)

# and file executable
add_executable(${PROJECT_NAME} main.cpp)

find_package(SFML 2.5.1 COMPONENTS system window graphics network audio REQUIRED)
target_link_libraries(${PROJECT_NAME} sfml-audio sfml-graphics sfml-window sfml-system)