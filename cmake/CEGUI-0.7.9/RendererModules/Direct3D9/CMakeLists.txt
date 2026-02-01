

add_subdirectory(DXSDK9)

file(GLOB D3D9_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Direct3D9/*.cpp)
file(GLOB D3D9_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Direct3D9/*.h)

add_library(CEGUIDirect3D9Renderer STATIC ${D3D9_SOURCES} ${D3D9_HEADERS})

target_include_directories(CEGUIDirect3D9Renderer PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Direct3D9/)


target_compile_definitions(CEGUIDirect3D9Renderer PRIVATE -DDIRECT3D9_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUIDirect3D9Renderer PRIVATE CEGUIBase dxsdk9)
set_library(CEGUIDirect3D9Renderer)