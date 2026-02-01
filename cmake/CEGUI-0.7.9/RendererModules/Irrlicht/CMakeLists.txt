

file(GLOB IRRLICHT_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Irrlicht/*.cpp)
file(GLOB IRRLICHT_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Irrlicht/*.h)

add_library(CEGUIIrrlichtRenderer SHARED ${IRRLICHT_SOURCES} ${IRRLICHT_HEADERS})


target_compile_definitions(CEGUIIrrlichtRenderer PRIVATE -DIRRLICHT_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUIIrrlichtRenderer PRIVATE CEGUIBase)


find_package(Irrlicht REQUIRED)
target_include_directories(CEGUIIrrlichtRenderer PRIVATE ${IRRLICHT_INCLUDE_DIRS})
target_link_libraries(CEGUIIrrlichtRenderer PRIVATE ${IRRLICHT_LIBRARIES})
