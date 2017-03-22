cmake_minimum_required(VERSION 3.7)
set( CMAKE_VERBOSE_MAKEFILE on )
project(SDL2)

set(CMAKEIFY_SOURCE_ROOT "SDL2-2.0.5")
include_directories(${CMAKEIFY_SOURCE_ROOT}/include)

file(GLOB SDL_SOURCES 
  ${CMAKEIFY_SOURCE_ROOT}/src/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/audio/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/audio/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/audio/dummy/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/atomic/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/core/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/cpuinfo/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/dynapi/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/events/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/file/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/haptic/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/haptic/dummy/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/joystick/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/joystick/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/loadso/dlopen/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/power/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/power/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/filesystem/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/render/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/render/*/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/stdlib/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/thread/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/thread/pthread/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/timer/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/timer/unix/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/video/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/video/android/*.c)

add_library(SDL2 STATIC ${SDL_SOURCES})
target_compile_options(SDL2 PRIVATE -DGL_GLEXT_PROTOTYPES)

file(COPY ${CMAKEIFY_SOURCE_ROOT}/include/ DESTINATION ${CMAKEIFY_REDIST_INCLUDE_DIRECTORY}/include/SDL2)


