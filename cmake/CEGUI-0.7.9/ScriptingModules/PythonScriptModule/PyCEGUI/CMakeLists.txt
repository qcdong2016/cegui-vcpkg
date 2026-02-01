

file(GLOB PYCEGUI_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/PythonScriptModule/PyCEGUI/*.cpp)
file(GLOB PYCEGUI_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ScriptingModules/PythonScriptModule/PyCEGUI/*.h)

add_library(PyCEGUI SHARED ${PYCEGUI_SOURCES} ${PYCEGUI_HEADERS})


target_link_libraries(PyCEGUI PRIVATE CEGUIBase)


find_package(PythonLibs REQUIRED)
find_package(Boost REQUIRED COMPONENTS python)
target_include_directories(PyCEGUI PRIVATE ${PYTHON_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
target_link_libraries(PyCEGUI PRIVATE ${PYTHON_LIBRARIES} ${Boost_LIBRARIES})
