cmake_minimum_required(VERSION 3.23)
#Download ARM Toolchain
include(rpi-pico-tools.cmake)

#Locate toolchain and SDK
set(PICO_TOOLCHAIN_PATH ${CMAKE_SOURCE_DIR}/toolchain)
set(PICO_SDK_FETCH_FROM_GIT on)
include(pico_sdk_import.cmake)

#Declare the project
project(hackatum2022)

# Set the language standard to C11
set(CMAKE_C_STANDARD 11)

# Init SDK
set(PICO_BOARD pico_w)
pico_sdk_init()

# Add executable.
add_executable(blinky blinky.c)

#Naming
pico_set_program_name(blinky "blinky")
pico_set_program_version(blinky "0.1")

# Add the standard library to the build
target_link_libraries(blinky pico_stdlib pico_cyw43_arch_none)

#Generate UF2
pico_add_extra_outputs(blinky)

