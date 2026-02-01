

file(GLOB FALAGARD_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/WindowRendererSets/Falagard/*.cpp)
file(GLOB FALAGARD_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/WindowRendererSets/Falagard/*.h)

add_library(CEGUIFalagardWR STATIC ${FALAGARD_SOURCES} ${FALAGARD_HEADERS})
target_include_directories(CEGUIFalagardWR PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/WindowRendererSets/Falagard/)

target_link_libraries(CEGUIFalagardWR PRIVATE CEGUIBase)
set_library(CEGUIFalagardWR)