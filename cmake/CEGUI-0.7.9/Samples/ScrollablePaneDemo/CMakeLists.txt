


file(GLOB SCROLLABLE_PANE_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/ScrollablePaneDemo/*.cpp)
file(GLOB SCROLLABLE_PANE_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/ScrollablePaneDemo/*.h)


add_executable(ScrollablePaneDemo ${SCROLLABLE_PANE_DEMO_SOURCES} ${SCROLLABLE_PANE_DEMO_HEADERS})
set_library(ScrollablePaneDemo)

target_include_directories(ScrollablePaneDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(ScrollablePaneDemo PRIVATE CEGUISampleHelper)


set_target_properties(ScrollablePaneDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
