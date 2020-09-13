cmake_minimum_required(VERSION 3.1.0)

# project number and version
project("Test Project"
    LANGUAGES CXX
    VERSION 1.0
    DESCRIPTION "Tutorial project description"
    )

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_COMPILER "g++" CACHE STRING "CXX compiler name")

add_executable(Tutorial Tutorial.cxx)

configure_file(TutorialConfig.h.in TutorialConfig.h)

install(TARGETS Tutorial DESTINATION bin)
install(FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"
    DESTINATION include
    )

target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                          )
