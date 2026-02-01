

find_package(wxWidgets CONFIG REQUIRED)


set(PROJ_DIR ${ROOT_DIR}/CEImagesetEditor-0.7.1)

include_directories(
    ${PROJ_DIR}/inc
)


set(SOURCES
    ${PROJ_DIR}/src/DialogAbout.cpp
    ${PROJ_DIR}/src/DialogResourceGroups.cpp
    ${PROJ_DIR}/src/ElasticBox.cpp
    ${PROJ_DIR}/src/ElasticBoxProperties.cpp
    ${PROJ_DIR}/src/ElasticBoxWindowRenderer.cpp
    ${PROJ_DIR}/src/CEImagesetEditor.cpp
    ${PROJ_DIR}/src/EditorDocument.cpp
    ${PROJ_DIR}/src/EditorFrame.cpp
    ${PROJ_DIR}/src/EditorGLCanvas.cpp
    ${PROJ_DIR}/src/EditorView.cpp
    ${PROJ_DIR}/src/ImagesetHandler.cpp
    ${PROJ_DIR}/src/PropertiesPanel.cpp
    ${PROJ_DIR}/src/wxPathCellEditor.cpp
)


add_definitions(
    -DPACKAGE_VERSION="0.7.1"
    -DEDITOR_DATA_DIR="${PROJ_DIR}")


add_executable(CEImagesetEditor ${SOURCES})


target_link_libraries(CEImagesetEditor PUBLIC
    wx::core 
    wx::base
    wx::gl

    CEGUIBase 
    CEGUIExpatParser 
    CEGUIOpenGLRenderer
    CEGUISTBImageCodec
    CEGUIFalagardWR
)

set_library(CEImagesetEditor)


set_target_properties(CEImagesetEditor PROPERTIES 
LINK_FLAGS "/SUBSYSTEM:WINDOWS /ENTRY:WinMainCRTStartup"
)
