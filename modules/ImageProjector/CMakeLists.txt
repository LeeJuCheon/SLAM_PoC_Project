################################################################################
# Project Name: ImageProjector
#
# Components:
#    - ExampleComponent: Wrapper class of ExampleLibrary
#
################################################################################

# Project information
cmake_minimum_required(VERSION 3.10)
set(PACKAGE_NAME ImageProjector)
project(${PACKAGE_NAME} LANGUAGES CXX)

# Export aliases
set(IMAGEPROJECTOR_PATH ${CMAKE_CURRENT_SOURCE_DIR} CACHE PATH "IMAGEPROJECTOR_PATH")
set(IMAGEPROJECTOR_INCLUDE_PATH
        "${IMAGEPROJECTOR_PATH}/include" CACHE PATH "IMAGEPROJECTOR_INCLUDE_PATH")
set(IMAGEPROJECTOR_RESOURCES_PATH
        "${IMAGEPROJECTOR_PATH}/resources" CACHE PATH "IMAGEPROJECTOR_RESOURCES_PATH")
set(IMAGEPROJECTOR_TEST_PATH
        "${IMAGEPROJECTOR_PATH}/test" CACHE PATH "IMAGEPROJECTOR_TEST_PATH")

# Paths
add_definitions(-DIMAGEPROJECTOR_SOURCE_DIR="${IMAGEPROJECTOR_PATH}")
add_definitions(-DIMAGEPROJECTOR_RESOURCES_DIR="${IMAGEPROJECTOR_RESOURCES_PATH}")

# Source files
set(IMAGEPROJECTOR_SOURCE_FILES
        src/ImageProjector.cpp
        )
add_library(${PACKAGE_NAME}
        ${IMAGEPROJECTOR_SOURCE_FILES}
        )

# Header files, including 3rdParty
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_MODULE_PATH})

target_include_directories(${PACKAGE_NAME} PUBLIC
        ${IMAGEPROJECTOR_INCLUDE_PATH}
        )
        
target_link_libraries(${PACKAGE_NAME} PUBLIC
        ${EASY_PROFILER_LIBS}
        ${SPDLOG_LIBS}
        stdc++fs
        )

# Compile options
target_compile_options(${PACKAGE_NAME} PRIVATE
        -Wall -Wextra -Wpedantic -Werror
        )
set_target_properties(${PACKAGE_NAME} PROPERTIES
        CXX_STANDARD 11
        CXX_STANDARD_REQUIRED ON
        CXX_EXTENSIONS OFF
        )

# Unit tests
add_subdirectory(test)
