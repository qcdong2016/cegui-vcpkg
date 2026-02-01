

file(GLOB EXPAT_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/XMLParserModules/expatParser/*.cpp)
file(GLOB EXPAT_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/XMLParserModules/expatParser/*.h)

add_library(CEGUIExpatParser STATIC ${EXPAT_SOURCES} ${EXPAT_HEADERS})

target_include_directories(CEGUIExpatParser PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/XMLParserModules/ExpatParser/)


target_link_libraries(CEGUIExpatParser PRIVATE CEGUIBase)


find_package(expat CONFIG REQUIRED)
target_link_libraries(CEGUIExpatParser PRIVATE expat::expat)
set_library(CEGUIExpatParser)