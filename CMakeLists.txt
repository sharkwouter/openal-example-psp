
## This file is a quick tutorial on writing CMakeLists for targeting the Vita
cmake_minimum_required(VERSION 2.8)


## Define project parameters here
# Name of the project
project(openal_test)

## Flags and includes for building
# Note that we make sure not to overwrite previous flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(MOJOAL_INCLUDE_DIR "$ENV{PSPDEV}/psp/include/mojoal")
set(SDL2_INCLUDE_DIR "$ENV{PSPDEV}/psp/include/mojoal")

# Add any additional include paths here
include_directories(
  ${MOJOAL_INCLUDE_DIR}
  ${SDL2_INCLUDE_DIR}
)

## Build and link
# Add all the files needed to compile here
add_executable(${PROJECT_NAME}
  openal-example.c
)

# Library to link to (drop the -l prefix). This will mostly be stubs.
target_link_libraries(${PROJECT_NAME}
  mojoal
  SDL2
  m
  GL
  pspvram
  ${PSP_LIBRARIES}
)

create_pbp_file(
    TARGET ${PROJECT_NAME}
    ICON_PATH NULL
    BACKGROUND_PATH NULL
    PREVIEW_PATH NULL
    TITLE OpenAL-Test
)
