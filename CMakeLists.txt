cmake_minimum_required(VERSION 3.6)
project(sift_test)

set(CMAKE_CXX_STANDARD 11)
set (CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH}
        /usr/local/opencv-3.2.0/share/OpenCV)

find_package (OpenCV 3.2.0 EXACT REQUIRED)

set(SOURCE_FILES main.cpp)
set(HOMOGRAPHY homography.cpp)

add_executable(sift_test ${SOURCE_FILES})
add_executable(homography ${HOMOGRAPHY} ${CMAKE_CURRENT_SOURCE_DIR}/Camera.cpp)

include_directories(${OpenCV_INCLUDE_DIRS})

target_include_directories (sift_test SYSTEM PUBLIC
        ${OpenCV_INCLUDE_DIRS})
target_include_directories (homography SYSTEM PUBLIC
        ${OpenCV_INCLUDE_DIRS})

target_link_libraries(sift_test ${OpenCV_LIBS})
target_link_libraries(homography ${OpenCV_LIBS})