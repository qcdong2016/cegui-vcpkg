

file(GLOB CORONA_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ImageCodecModules/CoronaImageCodec/*.cpp)
file(GLOB CORONA_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ImageCodecModules/CoronaImageCodec/*.h)

add_library(CEGUICoronaImageCodec STATIC ${CORONA_SOURCES} ${CORONA_HEADERS})


target_link_libraries(CEGUICoronaImageCodec PRIVATE CEGUIBase)


find_package(Corona REQUIRED)
target_include_directories(CEGUICoronaImageCodec PRIVATE ${CORONA_INCLUDE_DIRS})
target_link_libraries(CEGUICoronaImageCodec PRIVATE ${CORONA_LIBRARIES})
