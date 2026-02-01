

file(GLOB SILLY_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ImageCodecModules/SILLYImageCodec/*.cpp)
file(GLOB SILLY_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/SILLYImageCodec/*.h)

add_library(CEGUISILLYImageCodec STATIC ${SILLY_SOURCES} ${SILLY_HEADERS})
target_include_directories(CEGUISILLYImageCodec PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/SILLYImageCodec/)

target_link_libraries(CEGUISILLYImageCodec PRIVATE CEGUIBase)
set_library(CEGUISILLYImageCodec)