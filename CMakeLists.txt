## check c++11 / c++0x
include(CheckCXXCompilerFlag)
check_cxx_compiler_flag("-std=c++11" COMPILER_SUPPORTS_CXX11)
check_cxx_compiler_flag("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
else()
    message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()



cmake_minimum_required(VERSION 2.8.3)
project(hanp_layer_msgs)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  geometry_msgs
)

# find_package(Boost REQUIRED COMPONENTS system)


## install python modules and global scripts
# catkin_python_setup()

## add message, serviece and action files

add_message_files( DIRECTORY msg
  FILES
    TrackedHuman.msg
    TrackedHumans.msg
)

# add_service_files( DIRECTORY srv
#   FILES
#   Service1.srv
# )

# add_action_files( DIRECTORY action
#   FILES
#   Action1.action
# )

## generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
    geometry_msgs
)

## add dynamic reconfigure api
# generate_dynamic_reconfigure_options(
#   cfg/relative_path_to_file1.cfg
#   cfg/relative_path_to_file2.cfg
# )

## declare catkin package
catkin_package(
#   INCLUDE_DIRS
#     include
#  LIBRARIES
#    hanp_layer_msgs
  CATKIN_DEPENDS
    message_runtime
    geometry_msgs
#   DEPENDS
#     system_lib
)



## build ##

# include_directories(include)
# include_directories(
#   ${catkin_INCLUDE_DIRS}
# )

## declare a cpp library
# add_library(hanp_layer_msgs
#   src/${PROJECT_NAME}/hanp_layer_msgs.cpp
# )

## declare a cpp executable
# add_executable(hanp_layer_msgs_node
#   src/hanp_layer_msgs_node.cpp
# )

## cmake target dependencies of the executable/library
# add_dependencies(hanp_layer_msgs_node hanp_layer_msgs_generate_messages_cpp)

## build configure headers
# add_dependencies(hanp_layer_msgs_node ${PROJECT_NAME}_gencfg)

## libraries to link a library or executable target against
# target_link_libraries(hanp_layer_msgs_node
#   ${catkin_LIBRARIES}
# )



## install ##

## executable scripts (python etc.) for installation
# install(PROGRAMS
#   scripts/my_python_script
#   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## executables and/or libraries for installation
# install(TARGETS hanp_layer_msgs hanp_layer_msgs_node
#   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )

## cpp-header files for installation
# install(DIRECTORY include/${PROJECT_NAME}/
#   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
#   FILES_MATCHING PATTERN "*.h"
# )

## other files for installation (launch, data, bag files)
# foreach(dir launch data bags)
#    install(DIRECTORY ${dir}/
#       DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
# endforeach(dir)

## other files for installation
# install(FILES
#   # myfile1
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
# )



## testing ##

## add catch based cpp test target
# catkin_add_catchtest(${PROJECT_NAME}-test test/test_hanp_layer_msgs.cpp)
# if(TARGET ${PROJECT_NAME}-test)
#   target_link_libraries(${PROJECT_NAME}-test ${PROJECT_NAME})
# endif()

## add nosetest file folders
# catkin_add_nosetests(test)