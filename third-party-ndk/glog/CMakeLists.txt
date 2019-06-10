

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}  -Wwrite-strings -Woverloaded-virtual -Wno-sign-compare -DNDEBUG -g -O2
-D_START_GOOGLE_NAMESPACE_=\"namespace google {\" -D_END_GOOGLE_NAMESPACE_=\"}\" -DHAVE_PREAD=1")
set(CMAKE_CXX_FLAGS ${CMAKE_C_FLAGS})


include_directories(./)
include_directories(../)
include_directories(./glog/src)
file(GLOB SOURCE
        glog/src/demangle.cc
        glog/src/logging.cc
        glog/src/raw_logging.cc
        glog/src/signalhandler.cc
        glog/src/symbolize.cc
        glog/src/utilities.cc
        glog/src/vlog_is_on.cc)
add_library(glog
        SHARED
        ${SOURCE}
        )

# SET_TARGET_PROPERTIES(glog PROPERTIES LINKER_LANGUAGE C)