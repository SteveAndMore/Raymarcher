cmake_minimum_required(VERSION 3.10)
project(RayMarcherWithoutOpenGL)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include directories
include_directories(${CMAKE_SOURCE_DIR})

# Source files
set(SOURCES
    main.cpp
    geometry.cpp
    image.cpp
    maths.cpp
    scene.cpp
    vision.cpp
)

# Header files (optional, for IDEs)
set(HEADERS
    geometry.hpp
    image.hpp
    maths.hpp
    scene.hpp
    vision.hpp
)

# Find required OpenGL packages
find_package(OpenGL REQUIRED)

# You might need to adjust these if you're on Windows or Mac
find_package(GLEW REQUIRED)
find_package(GLUT REQUIRED)

# Create executable
add_executable(main ${SOURCES} ${HEADERS})

# Link libraries
target_link_libraries(main
    ${OPENGL_LIBRARIES}
    GLEW::GLEW
    GLUT::GLUT
    pthread
)

