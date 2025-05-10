# Quick Pico Build Guide (Windows, Hardcoded SDK Path)
https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-c-sdk.pdf

Watch my tutorial here: https://www.youtube.com/watch?v=W9v0iAhu0hc
Adapted from Low Level: Blink LED in C/C++ on the Raspberry Pi Pico [Linux SDK Setup] here: https://www.youtube.com/watch?v=JhajoAyP8e4&t=300s

1. Install tools:
   - Arm GNU Toolchain:
     https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads
     (Use: arm-gnu-toolchain-14.2.rel1-mingw-w64-x86_64-arm-none-eabi.exe)

   - CMake:
     https://cmake.org/download/

   - Ninja (build system):
     https://github.com/ninja-build/ninja/releases
     (Unzip and add ninja.exe to PATH)

   - elf2uf2 (for generating .uf2 files):
     https://sourceforge.net/projects/rpi-pico-utils/files/v1.3.0/elf2uf2.exe/download
     (Place in your project folder or a directory in PATH)

2. Clone SDK:
   git clone https://github.com/raspberrypi/pico-sdk.git
   cd pico-sdk
   git submodule update --init

3. Copy pico_sdk_import.cmake from:
   pico-sdk/external/ → your project folder

4. Put your blink.c, CMakeLists.txt, and pico_sdk_import.cmake in the same folder.

5. Edit CMakeLists.txt (see example file):

6. Build:
   mkdir build && cd build
   cmake .. -G "Ninja"
   ninja

7. Convert to .uf2:
   elf2uf2.exe blink.elf blink.uf2

8. Flash:
   Drag the .uf2 file to your Pico (hold BOOTSEL on plug-in)
