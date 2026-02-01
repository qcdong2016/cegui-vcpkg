


file(GLOB SAMPLE_HELPER_SOURCES ${CEGUI_ROOT_DIR}/Samples/common/src/*.cpp)
file(GLOB SAMPLE_HELPER_HEADERS ${CEGUI_ROOT_DIR}/Samples/common/include/*.h)


list(REMOVE_ITEM SAMPLE_HELPER_SOURCES ${CEGUI_ROOT_DIR}/Samples/common/src/MacCEGuiRendererSelector.cpp)
list(REMOVE_ITEM SAMPLE_HELPER_HEADERS ${CEGUI_ROOT_DIR}/Samples/common/include/MacCEGuiRendererSelector.h)
list(REMOVE_ITEM SAMPLE_HELPER_SOURCES ${CEGUI_ROOT_DIR}/Samples/common/src/GTK2CEGuiRendererSelector.cpp)
list(REMOVE_ITEM SAMPLE_HELPER_HEADERS ${CEGUI_ROOT_DIR}/Samples/common/include/GTK2CEGuiRendererSelector.h)
list(REMOVE_ITEM SAMPLE_HELPER_SOURCES ${CEGUI_ROOT_DIR}/Samples/common/src/CLICEGuiRendererSelector.cpp)
list(REMOVE_ITEM SAMPLE_HELPER_HEADERS ${CEGUI_ROOT_DIR}/Samples/common/include/CLICEGuiRendererSelector.h)


add_library(CEGUISampleHelper STATIC ${SAMPLE_HELPER_SOURCES} ${SAMPLE_HELPER_HEADERS})
set_library(CEGUISampleHelper)

target_compile_definitions(CEGUISampleHelper PRIVATE 
-DFREEGLUT_LIB_PRAGMAS=0
-DCEGUISAMPLE_EXPORTS)


target_include_directories(CEGUISampleHelper PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
)

find_package(GLUT REQUIRED)
target_link_libraries(CEGUISampleHelper PRIVATE GLUT::GLUT)

target_link_libraries(CEGUISampleHelper PUBLIC 
CEGUIBase 
CEGUIExpatParser 
CEGUIOpenGLRenderer
CEGUISTBImageCodec
CEGUIFalagardWR
)

if(WIN32)
    target_link_libraries(CEGUISampleHelper PRIVATE glu32 opengl32)
endif()


if(MSVC)
    source_group("Source Files" FILES ${SAMPLE_HELPER_SOURCES})
    source_group("Header Files" FILES ${SAMPLE_HELPER_HEADERS})
endif()
