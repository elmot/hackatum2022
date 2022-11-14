cmake_minimum_required(VERSION 3.24)
project(hackatum2022 C)

set(CMAKE_C_STANDARD 11)

add_executable(hackatum2022 main.c)

include(FetchContent)
FetchContent_Declare(rpi-pico-sdk
        URL https://github.com/raspberrypi/pico-sdk/archive/refs/tags/1.4.0.zip)
if(CMAKE_HOST_WIN32) #[[TODO  platform specific]]
    FetchContent_Declare(arm-toolchain
            URL https://developer.arm.com/-/media/Files/downloads/gnu/11.3.rel1/binrel/arm-gnu-toolchain-11.3.rel1-mingw-w64-i686-arm-none-eabi.zip
            URL_HASH SHA256=23f24595aa575fba4fdb0cb086df4b053862af60837502cb7e52bd4fb3d76c36)
elseif(CMAKE_HOST_LINUX)
    FetchContent_Declare(arm-toolchain
            URL https://developer.arm.com/-/media/Files/downloads/gnu/11.3.rel1/binrel/arm-gnu-toolchain-11.3.rel1-x86_64-arm-none-eabi.tar.xz
            URL_HASH SHA256=d420d87f68615d9163b99bbb62fe69e85132dc0a8cd69fca04e813597fe06121)
elseif(CMAKE_HOST_APPLE)
    FetchContent_Declare(arm-toolchain
            URL https://developer.arm.com/-/media/Files/downloads/gnu/11.3.rel1/binrel/arm-gnu-toolchain-11.3.rel1-darwin-x86_64-arm-none-eabi.tar.xz
            URL_HASH SHA256=826353d45e7fbaa9b87c514e7c758a82f349cb7fc3fd949423687671539b29cf)
else()
    message(FATAL_ERROR "Unsupported host system")
endif()
FetchContent_Populate(arm-toolchain)
FetchContent_Populate(rpi-pico-sdk)
