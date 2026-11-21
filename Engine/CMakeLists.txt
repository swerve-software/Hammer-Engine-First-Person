file(GLOB_RECURSE ENGINE_SRC CONFIGURE_DEPENDS *.cpp)

add_library(Engine STATIC ${ENGINE_SRC})

target_include_directories(Engine PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/Core
    ${CMAKE_CURRENT_SOURCE_DIR}/Platform
    ${CMAKE_CURRENT_SOURCE_DIR}/Renderer
    ${CMAKE_CURRENT_SOURCE_DIR}/Scene
    ${CMAKE_SOURCE_DIR}/lib/stb)


target_link_libraries(Engine PUBLIC glfw glad glm::glm)