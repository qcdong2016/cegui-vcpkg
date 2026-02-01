

file(GLOB D3D10_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Direct3D10/*.cpp)
file(GLOB D3D10_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Direct3D10/*.h)

add_library(CEGUIDirect3D10Renderer SHARED ${D3D10_SOURCES} ${D3D10_HEADERS})


target_compile_definitions(CEGUIDirect3D10Renderer PRIVATE -DDIRECT3D10_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUIDirect3D10Renderer PRIVATE CEGUIBase)
