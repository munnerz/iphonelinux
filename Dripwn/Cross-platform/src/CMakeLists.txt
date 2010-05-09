cmake_minimum_required(VERSION 2.6)

project (Dripwn)

# We want win32 executables to build staticly by default, since it's more difficult to keep the shared libraries straight on Windows
IF(WIN32)
	SET(BUILD_STATIC ON CACHE BOOL "Force compilation with static libraries")
ELSE(WIN32)
	SET(BUILD_STATIC OFF CACHE BOOL "Force compilation with static libraries")
ENDIF(WIN32)

include_directories (${PROJECT_SOURCE_DIR}/includes)
target_link_libraries (dripwn $$./MobileDevice.framework)

IF(BUILD_STATIC)
	SET(CMAKE_FIND_LIBRARY_SUFFIXES ".a")
ENDIF(BUILD_STATIC)

include_directories (${PROJECT_SOURCE_DIR}/includes)

add_executable(dripwn dripwn.c)