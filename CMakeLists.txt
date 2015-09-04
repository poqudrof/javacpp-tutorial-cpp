cmake_minimum_required (VERSION 2.6)
project (Tutorial)

set (Tutorial_VERSION_MAJOR 0)
set (Tutorial_VERSION_MINOR 1)

configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")
include_directories("${PROJECT_BINARY_DIR}/MathFunctions")

add_library(MathFunctions SHARED mysqrt.cxx)

add_executable(Tutorial tutorial.cxx)

target_link_libraries (Tutorial MathFunctions)

install (TARGETS Tutorial DESTINATION bin)
install (TARGETS MathFunctions DESTINATION lib)
install (FILES MathFunctions.h DESTINATION include)
