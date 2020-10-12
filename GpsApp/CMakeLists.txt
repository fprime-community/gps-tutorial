####
# GPS Tutorial 'GpsApp' Deployment CMakeLists.txt: GpsApp/CMakeLists.txt
#
# This sets up the build for the 'GpsApp' Application, including the custom
# components. In addition, it imports FPrime.cmake, which includes the core F Prime
# components.
#
# This file has several sections.
#
# 1. Header Section: define basic properties of the build
# 2. F prime core: includes all F prime core components, and build-system properties
# 3. Local subdirectories: contains all deployment specific directory additions
####

##
# Section 1: Basic Project Setup
#
# This contains the basic project information. Specifically, a cmake version and project definition. It also defines our
# default paths to the F prime framework, and sets a default toolchain.
##
project(GpsApp C CXX)  # Should match the directory it is in
cmake_minimum_required(VERSION 3.5)

##
# Section 2: F prime Core
#
# This includes all of the F prime core components, and imports the make-system. F prime core
# components will be placed in the F-Prime binary subdirectory to keep them from
# colliding with deployment specific items.
##
include("${FPRIME_FRAMEWORK_PATH}/cmake/FPrime.cmake")
# NOTE: register custom targets between these two lines
include("${FPRIME_FRAMEWORK_PATH}/cmake/FPrime-Code.cmake")


##
# Section 3: Components and Topology
#
# This section includes deployment specific directories. This allows use of non- core components in the topology,
# which is also added here.
##
# Add component subdirectories
add_fprime_subdirectory("${CMAKE_CURRENT_LIST_DIR}/Gps/")

# Add Topology subdirectory
add_fprime_subdirectory("${CMAKE_CURRENT_LIST_DIR}/Top/")
