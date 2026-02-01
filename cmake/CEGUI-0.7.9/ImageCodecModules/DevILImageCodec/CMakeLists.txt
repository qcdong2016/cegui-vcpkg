

file(GLOB DEVIL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ImageCodecModules/DevILImageCodec/*.cpp)
file(GLOB DEVIL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/DevILImageCodec/*.h)

add_library(CEGUIDevILImageCodec STATIC ${DEVIL_SOURCES} ${DEVIL_HEADERS})


target_link_libraries(CEGUIDevILImageCodec PRIVATE CEGUIBase)


find_package(DevIL REQUIRED)
target_include_directories(CEGUIDevILImageCodec PRIVATE ${IL_INCLUDE_DIRS})
target_link_libraries(CEGUIDevILImageCodec PRIVATE ${IL_LIBRARIES})
