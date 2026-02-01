

file(GLOB STB_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ImageCodecModules/STBImageCodec/*.cpp)
file(GLOB STB_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/STBImageCodec/*.h)

add_library(CEGUISTBImageCodec STATIC ${STB_SOURCES} ${STB_HEADERS})
target_include_directories(CEGUISTBImageCodec PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/STBImageCodec/)


target_link_libraries(CEGUISTBImageCodec PRIVATE CEGUIBase)
set_library(CEGUISTBImageCodec)