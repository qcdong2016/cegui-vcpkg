cmake_minimum_required(VERSION 3.20)

project(cegui-vcpkg)

set(ROOT_DIR ${CMAKE_CURRENT_LIST_DIR})
set(CEGUI_ROOT_DIR ${ROOT_DIR}/CEGUI-0.7.9)

add_subdirectory(cmake/CEGUI-0.7.9)
add_subdirectory(cmake/CEImagesetEditor-0.7.1)
add_subdirectory(cmake/CELayoutEditor-0.7.1)