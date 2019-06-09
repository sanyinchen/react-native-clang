cmake_minimum_required(VERSION 3.4.1)
project(react)

#set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=gnu99")


# Android 5.0 以上需要在此处设置 PIE
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIE")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -fPIE -pie")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DANDROID")
set(CMAKE_CXX_FLAGS ${CMAKE_C_FLAGS})

message(PARENT_CMAKE_C_FLAGS：${CMAKE_C_FLAGS})

# 配置使用 NDK Standalone Toolchain 编译
set(NDK_STANDALONE_TOOLCHAIN /home/sanyinchen/Android/Sdk/ndk-bundle/my-android-toolchain)
set(CMAKE_SYSTEM_NAME "armeabi-v7a x86 arm64-v8a x86_64")

set(CMAKE_SYSTEM_VERSION 16)
set(CMAKE_C_COMPILER ${NDK_STANDALONE_TOOLCHAIN}/bin/arm-linux-androideabi-gcc)
set(CMAKE_CXX_COMPILER ${NDK_STANDALONE_TOOLCHAIN}/bin/arm-linux-androideabi-g++)

#choose Android ABI. Mine is armeabi-v7a
set(CMAKE_ANDROID_ARCH_ABI armeabi-v7a)
set(CMAKE_FIND_ROOT_PATH ${NDK_STANDALONE_TOOLCHAIN})


# 使用 NDK 提供的头文件
add_definitions("--sysroot=${NDK_STANDALONE_TOOLCHAIN}/sysroot")

add_subdirectory(first-party/fb)
add_subdirectory(ReactCommon/cxxreact)
add_subdirectory(react/jni)


#
#aux_source_directory(react/jni SOURCE_FILES)
#
#add_executable(jni ${SOURCE_FILES})
#
#add_custom_target(jni COMMAND /home/sanyinchen/Android/Sdk/ndk-bundle/ndk-build NDK_APPLICATION_MK=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/src/main/jni/Application.mk NDK_OUT=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/build/tmp/buildReactNdkLib NDK_LIBS_OUT=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/build/react-ndk/all THIRD_PARTY_NDK_DIR=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/build/third-party-ndk REACT_COMMON_DIR=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/../ReactCommon REACT_SRC_DIR=/home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/src/main/java/com/facebook/react -C /home/sanyinchen/sanyinchen/workspace/android/AwesomeProject/android/react-native/ReactAndroid/src/main/jni/react/jni --jobs 12)