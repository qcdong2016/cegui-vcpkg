

file(GLOB D3D11_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/Direct3D11/*.cpp)
file(GLOB D3D11_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Direct3D11/*.h)

add_library(CEGUIDirect3D11Renderer SHARED ${D3D11_SOURCES} ${D3D11_HEADERS})

target_include_directories(CEGUIDirect3D11Renderer PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/RendererModules/Direct3D11/)

target_compile_definitions(CEGUIDirect3D11Renderer PRIVATE -DDIRECT3D11_GUIRENDERER_EXPORTS)


target_link_libraries(CEGUIDirect3D11Renderer PRIVATE CEGUIBase)


if(WIN32)
    target_link_libraries(CEGUIDirect3D11Renderer PRIVATE d3d11 dxgi d3dcompiler)
endif()
