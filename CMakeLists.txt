cmake_minimum_required(VERSION 3.4.1)

# Set the name of the project and store it in PROJECT_NAME. Also set the following variables:
project(soundtouch)

set (soundtouch_sources

    source/SoundTouch/AAFilter.cpp
    source/SoundTouch/FIFOSampleBuffer.cpp
    source/SoundTouch/FIRFilter.cpp
    source/SoundTouch/cpu_detect_x86.cpp
    source/SoundTouch/sse_optimized.cpp
    source/SoundStretch/WavFile.cpp
    source/SoundTouch/RateTransposer.cpp
    source/SoundTouch/SoundTouch.cpp
    source/SoundTouch/InterpolateCubic.cpp
    source/SoundTouch/InterpolateLinear.cpp
    source/SoundTouch/InterpolateShannon.cpp
    source/SoundTouch/TDStretch.cpp
    source/SoundTouch/BPMDetect.cpp
    source/SoundTouch/PeakFinder.cpp

)

add_library(soundtouch ${soundtouch_sources})

# Specify directories which the compiler should look for headers
target_include_directories(soundtouch
        PRIVATE source
        PUBLIC include source/SoundStretch)

# Compile Flags:
target_compile_options(soundtouch
        PRIVATE
        -fvisibility=hidden -fdata-sections -ffunction-sections
        -Wmacro-redefined)

target_link_libraries(soundtouch PRIVATE log android)
