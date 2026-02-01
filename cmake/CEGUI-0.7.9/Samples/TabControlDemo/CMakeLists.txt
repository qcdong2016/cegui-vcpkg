


file(GLOB TAB_CONTROL_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/TabControlDemo/*.cpp)
file(GLOB TAB_CONTROL_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/TabControlDemo/*.h)


add_executable(TabControlDemo ${TAB_CONTROL_DEMO_SOURCES} ${TAB_CONTROL_DEMO_HEADERS})
set_library(TabControlDemo)

target_include_directories(TabControlDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(TabControlDemo PRIVATE CEGUISampleHelper)


set_target_properties(TabControlDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
