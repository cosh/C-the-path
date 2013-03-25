PROJECT(C-THE-PATH)

cmake_minimum_required(VERSION 2.8)

INCLUDE(CheckIncludeFiles)
INCLUDE(CheckFunctionExists)
INCLUDE(CheckTypeSize)
INCLUDE(CTest)
INCLUDE(InstallRequiredSystemLibraries)

ENABLE_TESTING()

SET(CPACK_PACKAGE_VERSION_MAJOR "0")
SET(CPACK_PACKAGE_VERSION_MINOR "1")
SET(CPACK_PACKAGE_VERSION_PATCH "0")
SET(CPACK_PACKAGE_VENDOR "Henning Rauch")
SET(CPACK_RESOURCE_FILE_LICENSE LICENSE.txt)

INCLUDE(CPack)


add_subdirectory (Dependencies)

# Make sure the compiler can find include files from the F8 library.
include_directories (${PATH_SOURCE_DIR})

# Make sure the linker can find the F8 library once it is built.
link_directories (${PATH_BINARY_DIR})

# Add executable called "ctp" that is built from the source files
# "demo.cxx" and "demo_b.cxx".  The extensions are automatically found.
add_executable (ctp demo.cxx demo_b.cxx)

# Link the executable to the F8 library.
target_link_libraries (ctp PATH)
