cmake_minimum_required(VERSION 3.15)
project(CicadaMedia)
add_subdirectory(cmdline)


if (${CMAKE_SYSTEM_NAME} MATCHES "Windows")
else ()
    set(CMAKE_CXX_FLAGS "-fprofile-instr-generate -fcoverage-mapping")
endif ()

if (${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
    set(TARGET_PLATFORM macOSX)
elseif (${CMAKE_SYSTEM_NAME} MATCHES "Linux")
    set(TARGET_PLATFORM Linux)
elseif (${CMAKE_SYSTEM_NAME} MATCHES "Windows")
    set(TARGET_PLATFORM windows)
endif ()

include(framework/${TARGET_PLATFORM}.cmake)
#if (BUILD_TEST)
add_subdirectory(mediaPlayer/tests)
add_subdirectory(framework/tests)
#endif ()
