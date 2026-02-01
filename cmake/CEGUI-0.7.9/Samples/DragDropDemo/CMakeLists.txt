


file(GLOB DRAGDROP_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/DragDropDemo/*.cpp)
file(GLOB DRAGDROP_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/DragDropDemo/*.h)


add_executable(DragDropDemo ${DRAGDROP_DEMO_SOURCES} ${DRAGDROP_DEMO_HEADERS})
set_library(DragDropDemo)

target_include_directories(DragDropDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(DragDropDemo PRIVATE CEGUISampleHelper)


set_target_properties(DragDropDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
