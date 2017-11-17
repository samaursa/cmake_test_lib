cmake_minimum_required(VERSION 3.1)

project(TestLib)

set(TestLib_PUBLIC_HEADERS
  "include/LibA/FileA.h"
  "include/LibA/FileB.h"
  "include/LibA/FileC.h"
  )

set(TestLib_SOURCE_FILES
  "src/FileA.cpp"
  "src/FileB.cpp"
  "src/FileC.cpp"
  )

add_library(LibA
  ${TestLib_PUBLIC_HEADERS}
  ${TestLib_SOURCE_FILES}
  )

target_include_directories(LibA PUBLIC
      $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/>
      $<INSTALL_INTERFACE:include>  # <prefix>/include/mylib
  )

install(TARGETS LibA
  EXPORT LibAConfig
  PUBLIC_HEADER DESTINATION include/
  LIBRARY DESTINATION lib/LibA/
  ARCHIVE DESTINATION lib/LibA/static
  )

install(EXPORT LibAConfig
  NAMESPACE tl_
  DESTINATION cmake/
  )

install(DIRECTORY include/ DESTINATION include/)

export(TARGETS LibA FILE LibAConfig.cmake)
export(PACKAGE LibA)
