


file(GLOB DEMO8_SOURCES ${CEGUI_ROOT_DIR}/Samples/Demo8/*.cpp)
file(GLOB DEMO8_HEADERS ${CEGUI_ROOT_DIR}/Samples/Demo8/*.h)


add_executable(Demo8 ${DEMO8_SOURCES} ${DEMO8_HEADERS})
set_library(Demo8)

target_include_directories(Demo8 PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(Demo8 PRIVATE CEGUISampleHelper)


set_target_properties(Demo8 PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
