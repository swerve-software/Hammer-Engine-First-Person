cmake_minimum_required(VERSION 3.20)
project(SpannerEngineFirstPerson LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin)

if(MSVC)
    add_compile_options(/utf-8)
endif()

# GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(lib/GLFW)

# GLM
add_subdirectory(lib/GLM)

# GLAD
add_library(glad STATIC lib/GLAD/src/glad.c)
target_include_directories(glad PUBLIC lib/GLAD/include)

# ImGui
add_library(imgui STATIC
    lib/ImGui/imgui.cpp
    lib/ImGui/imgui_draw.cpp
    lib/ImGui/imgui_tables.cpp
    lib/ImGui/imgui_widgets.cpp
    lib/ImGui/imgui_impl_glfw.cpp
    lib/ImGui/imgui_impl_opengl3.cpp)
target_include_directories(imgui PUBLIC lib/ImGui)
target_link_libraries(imgui PUBLIC glfw)

add_subdirectory(Engine)
add_subdirectory(Editor)