

file(GLOB NULL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Null/*.cpp)
file(GLOB NULL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Null/*.h)

add_library(CEGUINullRenderer STATIC ${NULL_SOURCES} ${NULL_HEADERS})
target_include_directories(CEGUINullRenderer PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Null/)

target_compile_definitions(CEGUINullRenderer PRIVATE -DNULL_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUINullRenderer PRIVATE CEGUIBase)
set_library(CEGUINullRenderer)