cmake_minimum_required(VERSION 3.12)

set(PROJECT_NAME blink)                                       # <-- Update This To Match your .c filename
set(PICO_SDK_PATH "C:/Users/cpero/Documents/Pico/pico-sdk")   # <-- Update to match path to your pic-sdk folder
set(PICO_BUILD_TOOLS ON)

include(pico_sdk_import.cmake)

project(${PROJECT_NAME} C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(${PROJECT_NAME}
    ${PROJECT_SOURCE_DIR}/${PROJECT_NAME}.c
)

target_link_libraries(${PROJECT_NAME} pico_stdlib)

set(PICO_NO_PICOTOOL 1)

pico_add_extra_outputs(${PROJECT_NAME})
