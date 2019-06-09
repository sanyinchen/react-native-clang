


set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DLOG_TAG=\"ReactNative\"")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fexceptions -frtti -Wno-unused-lambda-capture")
set(CMAKE_CXX_FLAGS ${CMAKE_C_FLAGS})

include_directories(..)
include_directories(../../third-party-ndk/folly/)

file(GLOB SOURCE ./*.cpp)
add_library(reactnative
        STATIC
        ${SOURCE}
        )

target_link_libraries(reactnative
        boost
        jsinspector
        libfolly_json
        glog
        )