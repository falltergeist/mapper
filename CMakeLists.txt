cmake_minimum_required(VERSION 3.13)

project(mapper)
set(CMAKE_CXX_STANDARD 14)

find_package(OpenGL REQUIRED)

set(SOURCE_FILES
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/imgui.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/imgui_draw.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/imgui_widgets.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/imgui_tables.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/imgui.h
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/backends/imgui_impl_sdl3.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/backends/imgui_impl_sdl3.h
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/backends/imgui_impl_opengl3.cpp
        ${PROJECT_SOURCE_DIR}/thirdparty/imgui/backends/imgui_impl_opengl3.h
        ${PROJECT_SOURCE_DIR}/src/main.cpp
)

add_executable(${PROJECT_NAME} ${SOURCE_FILES})

target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR}/thirdparty/imgui)
target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR}/thirdparty/imgui/backends)
target_include_directories(${PROJECT_NAME} PUBLIC ${OPENGL_INCLUDE_DIR})
target_include_directories(${PROJECT_NAME} PUBLIC ${GLEW_INCLUDE_DIRS})

# SDL3
add_subdirectory(thirdparty/SDL)

target_link_libraries(
    ${PROJECT_NAME}
    SDL3::SDL3
    OpenGL::GL
)