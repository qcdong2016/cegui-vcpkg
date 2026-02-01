

file(GLOB TGA_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ImageCodecModules/TGAImageCodec/*.cpp)
file(GLOB TGA_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/TGAImageCodec/*.h)

add_library(CEGUITGAImageCodec STATIC ${TGA_SOURCES} ${TGA_HEADERS})
target_include_directories(CEGUITGAImageCodec PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/TGAImageCodec/)


target_link_libraries(CEGUITGAImageCodec PRIVATE CEGUIBase)
set_library(CEGUITGAImageCodec)