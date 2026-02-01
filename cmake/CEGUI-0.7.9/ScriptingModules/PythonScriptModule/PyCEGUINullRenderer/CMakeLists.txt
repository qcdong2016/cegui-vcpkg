

file(GLOB PYCEGUI_NULL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/PythonScriptModule/PyCEGUINullRenderer/*.cpp)
file(GLOB PYCEGUI_NULL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ScriptingModules/PythonScriptModule/PyCEGUINullRenderer/*.h)

add_library(PyCEGUINullRenderer SHARED ${PYCEGUI_NULL_SOURCES} ${PYCEGUI_NULL_HEADERS})


target_link_libraries(PyCEGUINullRenderer PRIVATE CEGUIBase CEGUINullRenderer PyCEGUI)


find_package(PythonLibs REQUIRED)
find_package(Boost REQUIRED COMPONENTS python)
target_include_directories(PyCEGUINullRenderer PRIVATE ${PYTHON_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
target_link_libraries(PyCEGUINullRenderer PRIVATE ${PYTHON_LIBRARIES} ${Boost_LIBRARIES})
