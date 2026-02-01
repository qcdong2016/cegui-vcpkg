cmake_minimum_required(VERSION 3.10)
project(CELayoutEditor VERSION 0.7.1)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(PROJ_DIR ${ROOT_DIR}/CELayoutEditor-0.7.1)


include_directories(
    ${PROJ_DIR}/inc
    ${PROJ_DIR}/dependencies/iniFile
)


find_package(wxWidgets CONFIG REQUIRED)


set(SOURCE_FILES
    ${PROJ_DIR}/dependencies/iniFile/iniFile.cpp
    ${PROJ_DIR}/src/CELayoutEditor.cpp
    ${PROJ_DIR}/src/CommandAddWindow.cpp
    ${PROJ_DIR}/src/CopiedSelection.cpp
    ${PROJ_DIR}/src/DialogAbout.cpp
    ${PROJ_DIR}/src/DialogAddWindow.cpp
    ${PROJ_DIR}/src/DialogGrid.cpp
    ${PROJ_DIR}/src/DialogMain.cpp
    ${PROJ_DIR}/src/EditorCanvas.cpp
    ${PROJ_DIR}/src/EditorDocument.cpp
    ${PROJ_DIR}/src/EditorFrame.cpp
    ${PROJ_DIR}/src/EditorView.cpp
    ${PROJ_DIR}/src/ExceptionManager.cpp
    ${PROJ_DIR}/src/Options.cpp
    ${PROJ_DIR}/src/Selection.cpp
    ${PROJ_DIR}/src/SelectionMover.cpp
    ${PROJ_DIR}/src/WindowBox.cpp
    ${PROJ_DIR}/src/WindowContext.cpp
    ${PROJ_DIR}/src/SimpleSymbolEngine.cpp
)


if(WIN32)
    list(APPEND SOURCE_FILES
        ${PROJ_DIR}/src/pch.cpp
        ${PROJ_DIR}/src/SimpleSymbolEngine.cpp
    )
endif()


add_executable(CELayoutEditor ${SOURCE_FILES})


target_link_libraries(CELayoutEditor PUBLIC
    wx::core 
    wx::base
    wx::gl

    CEGUIBase 
    CEGUIExpatParser 
    CEGUIOpenGLRenderer
    CEGUISTBImageCodec
    CEGUIFalagardWR
)

set_library(CELayoutEditor)


set_target_properties(CELayoutEditor PROPERTIES 
LINK_FLAGS "/SUBSYSTEM:WINDOWS /ENTRY:WinMainCRTStartup"
)