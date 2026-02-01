


file(GLOB TEXT_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/TextDemo/*.cpp)
file(GLOB TEXT_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/TextDemo/*.h)


add_executable(TextDemo ${TEXT_DEMO_SOURCES} ${TEXT_DEMO_HEADERS})
set_library(TextDemo)

target_include_directories(TextDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(TextDemo PRIVATE CEGUISampleHelper)


set_target_properties(TextDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
