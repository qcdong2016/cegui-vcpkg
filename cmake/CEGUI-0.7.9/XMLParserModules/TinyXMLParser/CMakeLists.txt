

file(GLOB TINYXML_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/XMLParserModules/TinyXMLParser/*.cpp)
file(GLOB TINYXML_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/XMLParserModules/TinyXMLParser/*.h)

add_library(CEGUITinyXMLParser STATIC ${TINYXML_SOURCES} ${TINYXML_HEADERS})


target_link_libraries(CEGUITinyXMLParser PRIVATE CEGUIBase)
