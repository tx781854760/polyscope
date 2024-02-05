cmake_minimum_required(VERSION 3.5...3.22)

project(polyscope)

### Policy settings
cmake_policy(SET CMP0054 NEW)   # don't implicitly dereference inside if()

## Project options

# Backend
set(POLYSCOPE_BACKEND_OPENGL3_GLFW "ON" CACHE BOOL "Enable openGL3_glfw backend")
set(POLYSCOPE_BACKEND_OPENGL_MOCK "ON" CACHE BOOL "Enable openGL_mock backend")

### Do anything needed for dependencies and bring their stuff in to scope
find_package(args CONFIG REQUIRED)
find_package(glad CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)
find_package(imgui CONFIG REQUIRED)
find_package(nlohmann_json CONFIG REQUIRED)
find_package(Stb REQUIRED)

### Add things for this project
add_subdirectory(src)

find_package(libigl CONFIG REQUIRED)

# Deps
add_subdirectory(deps/geometry-central)
### Now we can link the target 'polyscope'
add_subdirectory(examples/demo-app)