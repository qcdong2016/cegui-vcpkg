


file(GLOB FONT_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/FontDemo/*.cpp)
file(GLOB FONT_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/FontDemo/*.h)


add_executable(FontDemo ${FONT_DEMO_SOURCES} ${FONT_DEMO_HEADERS})
set_library(FontDemo)

target_include_directories(FontDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(FontDemo PRIVATE CEGUISampleHelper)


set_target_properties(FontDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
