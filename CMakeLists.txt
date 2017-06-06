cmake_minimum_required(VERSION 3.2)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/)

project(hello_world Go)

set(SOURCE_FILES
    src/main.go)

add_executable(hello_world ${SOURCE_FILES})

SET (SVG_ICON_FILE "${CMAKE_SOURCE_DIR}/icon.svg")

SET( CPACK_PACKAGE_FILE_NAME "${PROJECT_NAME}" )
IF(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
  MESSAGE(STATUS "Running Mac packaging")
  INCLUDE("mac/packaging.cmake")
ELSEIF(${CMAKE_SYSTEM_NAME} MATCHES "Linux")
  MESSAGE(STATUS "Running Linux packaging")
  INCLUDE("ubuntu/packaging.cmake")
ENDIF()

INCLUDE( CPack )
