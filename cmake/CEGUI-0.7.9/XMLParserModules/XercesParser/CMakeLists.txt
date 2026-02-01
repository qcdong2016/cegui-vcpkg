

file(GLOB XERCES_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/XMLParserModules/XercesParser/*.cpp)
file(GLOB XERCES_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/XMLParserModules/XercesParser/*.h)

add_library(CEGUIXercesParser STATIC ${XERCES_SOURCES} ${XERCES_HEADERS})


target_link_libraries(CEGUIXercesParser PRIVATE CEGUIBase)


find_package(XercesC REQUIRED)
target_include_directories(CEGUIXercesParser PRIVATE ${XERCESC_INCLUDE_DIRS})
target_link_libraries(CEGUIXercesParser PRIVATE ${XERCESC_LIBRARIES})
