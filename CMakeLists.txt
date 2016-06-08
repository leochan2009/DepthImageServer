cmake_minimum_required(VERSION 2.8)
project( DepthImageServer )
get_filename_component(PARENT_DIR ${CMAKE_SOURCE_DIR} DIRECTORY)
set(VTK_DIR "${PARENT_DIR}/Slicer-unixBuild/VTKv6-build")
find_package(VTK REQUIRED)
include(${VTK_USE_FILE})

get_filename_component(PARENT_DIR ${CMAKE_SOURCE_DIR} DIRECTORY)
set(XH264_INCLUDE "${PARENT_DIR}/x264" CACHE STRING "x264 source file")
set(XH264_LIB "${PARENT_DIR}/x264" CACHE STRING "x264 library")

set(VTK_DIR "${PARENT_DIR}/Slicer-unixBuild/VTKv6-build")
find_package(VTK REQUIRED)
include(${VTK_USE_FILE})

include_directories("${OpenH264_INCLUDE}/codec")
include_directories("${OpenH264_INCLUDE}/res")
include_directories("${OpenH264_INCLUDE}/test")
LINK_DIRECTORIES("${OpenH264_LIB}")

set(OpenIGTLink_INCLUDE "${PARENT_DIR}/OpenIGTLink/Source" CACHE STRING "OpenIGTLink source file")
set(OpenIGTLink_LIB "${PARENT_DIR}/OpenIGTLink-XcodeBuild" CACHE STRING "OpenIGTLink library")

include_directories("${XH264_INCLUDE}")
LINK_DIRECTORIES("${XH264_lib}/bin")

find_package(Qt5 COMPONENTS Core REQUIRED QUIET)
add_executable(qtimageviewer ${Srcs})
qt5_use_modules(qtimageviewer Core Gui Widgets)

add_executable( DepthImageServer DepthImageServer.cxx)
target_link_libraries( DepthImageServer OpenIGTLink XH264_LIB ${VTK_LIBRARIES})

