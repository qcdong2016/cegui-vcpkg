


file(GLOB FIRST_WINDOW_SOURCES ${CEGUI_ROOT_DIR}/Samples/FirstWindow/*.cpp)
file(GLOB FIRST_WINDOW_HEADERS ${CEGUI_ROOT_DIR}/Samples/FirstWindow/*.h)


add_executable(FirstWindow ${FIRST_WINDOW_SOURCES} ${FIRST_WINDOW_HEADERS})
set_library(FirstWindow)

target_include_directories(FirstWindow PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(FirstWindow PRIVATE CEGUISampleHelper)


set_target_properties(FirstWindow PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
