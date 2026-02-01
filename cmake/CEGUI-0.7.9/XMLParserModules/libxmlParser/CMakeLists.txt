

file(GLOB LIBXML_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/XMLParserModules/libxmlParser/*.cpp)
file(GLOB LIBXML_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/XMLParserModules/libxmlParser/*.h)

add_library(CEGUILibxmlParser STATIC ${LIBXML_SOURCES} ${LIBXML_HEADERS})


target_link_libraries(CEGUILibxmlParser PRIVATE CEGUIBase)


find_package(LibXml2 REQUIRED)
target_include_directories(CEGUILibxmlParser PRIVATE ${LIBXML2_INCLUDE_DIR})
target_link_libraries(CEGUILibxmlParser PRIVATE ${LIBXML2_LIBRARIES})
