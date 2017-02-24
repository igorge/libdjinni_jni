cmake_minimum_required(VERSION 3.5)
project(djinni_jni)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra -Wno-deprecated -Wno-unused-parameter -fexceptions -frtti")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC")

if(ANDROID_STL)
    message (STATUS "ANDROID BUILD DETECTED")
else()
    find_package(JNI)

    if (JNI_FOUND)
        message (STATUS "JNI_INCLUDE_DIRS=${JNI_INCLUDE_DIRS}")
        message (STATUS "JNI_LIBRARIES=${JNI_LIBRARIES}")
    endif()
endif()



set(DJINNI_INCLUDE_DIRS ${JNI_INCLUDE_DIRS} ${PROJECT_SOURCE_DIR}/src/support-lib/jni)

include_directories(
        ${CMAKE_CURRENT_BINARY_DIR} ${PROJECT_SOURCE_DIR} ${JNI_INCLUDE_DIRS} ${PROJECT_SOURCE_DIR}/src/support-lib/jni ${gie_include_dir} )

set(SOURCE_FILES
        src/support-lib/jni/djinni_support.cpp
        src/support-lib/jni/djinni_main.cpp )

add_library(djinni_jni SHARED ${SOURCE_FILES})

target_link_libraries(djinni_jni)
