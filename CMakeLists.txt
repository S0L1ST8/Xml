cmake_minimum_required(VERSION 3.11)

project(xml CXX)
set(CMAKE_CXX_STANDARD 17)

include(${CMAKE_BINARY_DIR}/conanbuildinfo_multi.cmake)
conan_basic_setup(TARGETS)

add_executable(main main.cpp)

if(CMAKE_SYSTEM_NAME MATCHES "^MINGW")
  set(SYSTEM_LIBS -lstdc++)
else()
  set(SYSTEM_LIBS)
endif()

target_include_directories(main PRIVATE CONAN_PKG::pugixml)
target_link_libraries(main CONAN_PKG::pugixml)
target_link_libraries(main ${SYSTEM_LIBS})
