cmake_minimum_required (VERSION 3.16)

# projectname is the same as the main-executable
project(main)

add_definitions('-g')
add_definitions('-Wall')
#add_definitions('-std=c++11')

#============================================
find_package(Boost)
#   from cmake-modules:
#       FindBoost
#              Find Boost include dirs and libraries

#              Use this module by invoking find_package with the form:

#                 find_package(Boost
#                   [version] [EXACT]      # Minimum or EXACT version e.g. 1.67.0
#                   [REQUIRED]             # Fail with error if Boost is not found
#                   [COMPONENTS <libs>...] # Boost libraries by their canonical name
#                                          # e.g. "date_time" for "libboost_date_time"
#                   [OPTIONAL_COMPONENTS <libs>...]
#                                          # Optional Boost libraries by their canonical name)
#                   )                      # e.g. "date_time" for "libboost_date_time"

#              This module finds headers and requested component libraries OR a CMake package configuration file provided by a “Boost CMake” build.  For the lat‐
#              ter case skip to the “Boost CMake” section below.  For the former case results are reported in variables:

#                 Boost_FOUND            - True if headers and requested libraries were found
#                 Boost_INCLUDE_DIRS     - Boost include directories
#                 Boost_LIBRARY_DIRS     - Link directories for Boost libraries
#                 Boost_LIBRARIES        - Boost component libraries to be linked
#                 Boost_<C>_FOUND        - True if component <C> was found (<C> is upper-case)
#                 Boost_<C>_LIBRARY      - Libraries to link for component <C> (may include
#                                          target_link_libraries debug/optimized keywords)
#                 Boost_VERSION_MACRO    - BOOST_VERSION value from boost/version.hpp
#                 Boost_VERSION_STRING   - Boost version number in x.y.z format
#                 Boost_VERSION          - if CMP0093 NEW => same as Boost_VERSION_STRING
#                                          if CMP0093 OLD or unset => same as Boost_VERSION_MACRO
#                 Boost_LIB_VERSION      - Version string appended to library filenames
#                 Boost_VERSION_MAJOR    - Boost major version number (X in X.y.z)
#                                          alias: Boost_MAJOR_VERSION
#                 Boost_VERSION_MINOR    - Boost minor version number (Y in x.Y.z)
#                                          alias: Boost_MINOR_VERSION
#                 Boost_VERSION_PATCH    - Boost subminor version number (Z in x.y.Z)
#                                          alias: Boost_SUBMINOR_VERSION
#                 Boost_VERSION_COUNT    - Amount of version components (3)
#                 Boost_LIB_DIAGNOSTIC_DEFINITIONS (Windows)
#                                        - Pass to add_definitions() to have diagnostic
#                                          information about Boost's automatic linking
#                                          displayed during compilation

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)
message (STATUS
    "CMAKE_EXPORT_COMPILE_COMMANDS set to: "
    ${CMAKE_EXPORT_COMPILE_COMMANDS}
    )

#============================================
add_executable(${PROJECT_NAME}
    ${PROJECT_NAME}.cpp
    dispatcher.cpp
    request.cpp
    worker.cpp
)

#============================================
target_include_directories( ${PROJECT_NAME}
    PUBLIC
    ${Boost_INCLUDE_DIR}
    )
target_link_libraries(${PROJECT_NAME}
    PUBLIC
    ${Boost_LIBRARIES}
    )

