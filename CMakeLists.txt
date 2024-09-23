cmake_minimum_required(VERSION 3.24)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Set runtime linking to /MT
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
message(STATUS "Link against static runtime")

project(mozjs-78.9.0)

add_subdirectory(mozjs)

add_executable(hello boilerplate.cpp hello.cpp)
target_link_libraries(hello PRIVATE mozjs)

add_executable(cookbook boilerplate.cpp cookbook.cpp)
target_link_libraries(cookbook PRIVATE mozjs)

add_executable(modules boilerplate.cpp modules.cpp)
target_link_libraries(modules PRIVATE mozjs)
target_compile_options(modules PRIVATE /utf-8)

add_executable(tracing boilerplate.cpp tracing.cpp)
target_link_libraries(tracing PRIVATE mozjs)

#add_executable(repl boilerplate.cpp repl.cpp)
#target_link_libraries(repl PRIVATE mozjs)

#add_executable(resolve boilerplate.cpp resolve.cpp)
#target_link_libraries(resolve PRIVATE mozjs)