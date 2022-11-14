cmake_minimum_required(VERSION 3.23)
include(rpi-pico-tools.cmake)
set(PICO_TOOLCHAIN_PATH ${CMAKE_SOURCE_DIR}/toolchain)

set(PICO_SDK_FETCH_FROM_GIT on)

include(pico_sdk_import.cmake)
project(hackatum2022)

set(CMAKE_C_STANDARD 11)
pico_sdk_init()

#todo request python!
