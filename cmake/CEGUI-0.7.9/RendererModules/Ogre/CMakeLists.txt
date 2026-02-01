

file(GLOB OGRE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Ogre/*.cpp)
file(GLOB OGRE_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Ogre/*.h)

add_library(CEGUIOgreRenderer SHARED ${OGRE_SOURCES} ${OGRE_HEADERS})


target_compile_definitions(CEGUIOgreRenderer PRIVATE -DOGRE_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUIOgreRenderer PRIVATE CEGUIBase)


find_package(OGRE REQUIRED)
target_include_directories(CEGUIOgreRenderer PRIVATE ${OGRE_INCLUDE_DIRS})
target_link_libraries(CEGUIOgreRenderer PRIVATE ${OGRE_LIBRARIES})


find_package(OIS REQUIRED)
target_include_directories(CEGUIOgreRenderer PRIVATE ${OIS_INCLUDE_DIRS})
target_link_libraries(CEGUIOgreRenderer PRIVATE ${OIS_LIBRARIES})
