


file(GLOB TREE_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/TreeDemo/*.cpp)
file(GLOB TREE_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/TreeDemo/*.h)


add_executable(TreeDemo ${TREE_DEMO_SOURCES} ${TREE_DEMO_HEADERS})
set_library(TreeDemo)

target_include_directories(TreeDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(TreeDemo PRIVATE CEGUISampleHelper)


set_target_properties(TreeDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
