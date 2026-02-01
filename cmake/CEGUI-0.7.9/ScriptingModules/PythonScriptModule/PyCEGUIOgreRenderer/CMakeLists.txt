

file(GLOB PYCEGUI_OGRE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/PythonScriptModule/PyCEGUIOgreRenderer/*.cpp)
file(GLOB PYCEGUI_OGRE_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ScriptingModules/PythonScriptModule/PyCEGUIOgreRenderer/*.h)

add_library(PyCEGUIOgreRenderer SHARED ${PYCEGUI_OGRE_SOURCES} ${PYCEGUI_OGRE_HEADERS})


target_link_libraries(PyCEGUIOgreRenderer PRIVATE CEGUIBase CEGUIOgreRenderer PyCEGUI)


find_package(PythonLibs REQUIRED)
find_package(Boost REQUIRED COMPONENTS python)
target_include_directories(PyCEGUIOgreRenderer PRIVATE ${PYTHON_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
target_link_libraries(PyCEGUIOgreRenderer PRIVATE ${PYTHON_LIBRARIES} ${Boost_LIBRARIES})
