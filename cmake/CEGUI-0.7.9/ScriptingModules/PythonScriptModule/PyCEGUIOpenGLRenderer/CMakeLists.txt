

file(GLOB PYCEGUI_OPENGL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/PythonScriptModule/PyCEGUIOpenGLRenderer/*.cpp)
file(GLOB PYCEGUI_OPENGL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ScriptingModules/PythonScriptModule/PyCEGUIOpenGLRenderer/*.h)

add_library(PyCEGUIOpenGLRenderer SHARED ${PYCEGUI_OPENGL_SOURCES} ${PYCEGUI_OPENGL_HEADERS})


target_link_libraries(PyCEGUIOpenGLRenderer PRIVATE CEGUIBase CEGUIOpenGLRenderer PyCEGUI)


find_package(PythonLibs REQUIRED)
find_package(Boost REQUIRED COMPONENTS python)
target_include_directories(PyCEGUIOpenGLRenderer PRIVATE ${PYTHON_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
target_link_libraries(PyCEGUIOpenGLRenderer PRIVATE ${PYTHON_LIBRARIES} ${Boost_LIBRARIES})
