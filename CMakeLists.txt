# This is the main CMake file for IO-meter.
#
# Ed Hartnett, 4/5/22
cmake_minimum_required(VERSION 3.15)

# Get the version.
file(STRINGS "VERSION" pVersion)
project(io-meter VERSION ${pVersion} LANGUAGES C Fortran)

# Find CMake code.
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Handle user options.
option(ENABLE_DOCS "Enable generation of doxygen-based documentation." OFF)

if(NOT CMAKE_BUILD_TYPE MATCHES "^(Debug|Release|RelWithDebInfo|MinSizeRel)$")
  message(STATUS "Setting build type to 'Release' as none was specified.")
  set(CMAKE_BUILD_TYPE
      "Release"
      CACHE STRING "Choose the type of build." FORCE)
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release"
                                               "MinSizeRel" "RelWithDebInfo")
endif()

include(GNUInstallDirs)

# Find packages.
find_package(NetCDF 4.3.3 REQUIRED C)
find_package(MPI REQUIRED C)

# Determine whether or not to generate documentation.
if(ENABLE_DOCS)
  find_package(Doxygen REQUIRED)
  add_subdirectory(docs)  
endif()

add_subdirectory(src)

# Turn on tests.
#include(CTest)
#if(BUILD_TESTING)
#  add_subdirectory(tests)
#endif()


