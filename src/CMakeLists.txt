SET(CTP_SRC ${CTP_SRC}
  demo.cxx
  demo_b.cxx
)

# Make sure the compiler can find include files from the F8 library.
INCLUDE_DIRECTORIES (${PATH_SOURCE_DIR}/include)
# Make sure the linker can find the F8 library once it is built.
LINK_DIRECTORIES(${PATH_BINARY_DIR})

# Add executable called "ctp" that is built from the source files
# "demo.cxx" and "demo_b.cxx".  The extensions are automatically found.
ADD_EXECUTABLE(ctp  ${CTP_SRC})

# Link the executable to the F8 library.
TARGET_LINK_LIBRARIES(ctp PATH)

INSTALL(TARGETS ctp
        RUNTIME DESTINATION bin
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib
        )

