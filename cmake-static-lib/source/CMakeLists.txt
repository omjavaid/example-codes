# Set the project name and version
cmake_minimum_required(VERSION 3.16)
project(testlib)

# Add the source files for the library
add_library(testlib STATIC obj1.cpp obj2.cpp obj3.cpp)

# Set the include directories for the library
target_include_directories(testlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

# Set the properties of the library
set_target_properties(testlib PROPERTIES
  OUTPUT_NAME "testlib"
  ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/lib"
)

# Set the install location for the library and header files
install(TARGETS testlib
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib
        RUNTIME DESTINATION bin)

install(FILES testlib.h DESTINATION include)

# Add the source files for the sample application
add_executable(testapp main.cpp)

# Link the sample application against the mylib library
target_link_libraries(testapp testlib)

# Set the properties of the sample application
set_target_properties(testapp PROPERTIES
  OUTPUT_NAME "testapp"
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/bin"
)

# Set the install location for the sample application
install(TARGETS testapp DESTINATION bin)