cmake_minimum_required(VERSION 3.0)
project(Ascension)

#set(CMAKE_BUILD_TYPE Release)
set(CMAKE_CXX_STANDARD 11)


find_package(OpenGL REQUIRED)

# Compile external dependencies
add_subdirectory(external)

include_directories(
        external/glfw/include/
        external/glm/
        external/glew/include/
        .
)

set(ALL_LIBS
        ${OPENGL_LIBRARY}
        glfw
        glew
        )

add_definitions(
        -DTW_STATIC
        -DTW_NO_LIB_PRAGMA
        -DTW_NO_DIRECT3D
        -DGLEW_STATIC
        -D_CRT_SECURE_NO_WARNINGS
)

# Source files
set(src main.cpp)

# exe
add_executable(${PROJECT_NAME} ${src})
target_link_libraries(${PROJECT_NAME} ${ALL_LIBS})