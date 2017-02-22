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
  ${CMAKEIFY_SOURCE_ROOT}/atomic/SDL_atomic.c
  ${CMAKEIFY_SOURCE_ROOT}/atomic/SDL_spinlock.c.arm
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
  ${CMAKEIFY_SOURCE_ROOT}/src/video/android/*.c
  ${CMAKEIFY_SOURCE_ROOT}/src/test/*.c)

add_library(SDL2 SHARED ${SDL_SOURCES})
target_compile_options(SDL2 PRIVATE -DGL_GLEXT_PROTOTYPES)
target_link_libraries(SDL2 PRIVATE dl GLESv1_CM GLESv2 log android)

