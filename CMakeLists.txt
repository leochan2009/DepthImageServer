cmake_minimum_required(VERSION 2.8)
project( DepthImageServer )

set(OpenH264_INCLUDE "/Users/longquanchen/Desktop/Github/OpenIGTLink-xcodeBuild/Testing/OpenH264" CACHE STRING "OpenH264 source file")
set(OpenH264_LIB "/Users/longquanchen/Desktop/Github/OpenIGTLink-xcodeBuild/Testing/OpenH264" CACHE STRING "OpenH264 library")

include_directories("${OpenH264_INCLUDE}/codec")
include_directories("${OpenH264_INCLUDE}/res")
include_directories("${OpenH264_INCLUDE}/test")
LINK_DIRECTORIES("${OpenH264_LIB}")

set(OpenIGTLink_INCLUDE "/Users/longquanchen/Desktop/Github/OpenIGTLink/Source" CACHE STRING "OpenIGTLink source file")
set(OpenIGTLink_LIB "/Users/longquanchen/Desktop/Github/OpenIGTLink-xcodeBuild" CACHE STRING "OpenIGTLink library")

include_directories("${OpenIGTLink_INCLUDE}")
include_directories("${OpenIGTLink_INCLUDE}/igtlutil")
include_directories("${OpenIGTLink_LIB}")
message(${OpenIGTLink_LIB})
LINK_DIRECTORIES("${OpenIGTLink_LIB}/bin")

add_executable( DepthImageServer DepthImageServer.cxx)
target_link_libraries( DepthImageServer OpenIGTLink openh264)

