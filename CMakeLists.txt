cmake_minimum_required(VERSION 3.15)

set(MAIN_TARGET_NAME constexpr-hash-map)
set(MAIN_TARGET_FOLDER_NAME constexpr-hash-map)
set(PROJECT_VERSION 1.2.0)

# set the project name
project(${MAIN_TARGET_NAME} LANGUAGES CXX VERSION ${PROJECT_VERSION})

# Set C++ Version
set(CMAKE_CXX_STANDARD 20)

# Set Default PREFIX
if(NOT DEFINED CMAKE_INSTALL_PREFIX)
        Message("CMAKE_INSTALL_PREFIX set to \"../bin\"")
        set(CMAKE_INSTALL_PREFIX "../bin")
else(NOT DEFINED CMAKE_INSTALL_PREFIX)
        Message("CMAKE_INSTALL_PREFIX was: " ${CMAKE_INSTALL_PREFIX})
endif(NOT DEFINED CMAKE_INSTALL_PREFIX)

#Make Library
add_library(${MAIN_TARGET_NAME} INTERFACE)
set_target_properties(${MAIN_TARGET_NAME} PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(${MAIN_TARGET_NAME} PROPERTIES SOVERSION 1)

option(BUILD_SHARED_LIBS "Build Project with Shared Libraries" ON)

set(LIBRARY_OUTPUT_PATH "${CMAKE_BINARY_DIR}")
set(EXECUTABLE_OUTPUT_PATH "${CMAKE_BINARY_DIR}")

# Debug Option (define DEBUG as 1 if this DEBUG option is true or if cmake is run as Debug)
option(DEBUG "Is Compile for DEBUG" ON)
target_compile_definitions(${MAIN_TARGET_NAME} INTERFACE DEBUG=$<IF:$<OR:$<BOOL:DEBUG>, $<CONFIG:Debug>>,1,0>)

add_subdirectory(include)

INSTALL(TARGETS ${MAIN_TARGET_NAME} 
        DESTINATION lib/${MAIN_TARGET_FOLDER_NAME}
        FILE_SET HEADERS DESTINATION include/${MAIN_TARGET_FOLDER_NAME}
)