cmake_minimum_required(VERSION 2.8)

project (C-THE-PATH)

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
