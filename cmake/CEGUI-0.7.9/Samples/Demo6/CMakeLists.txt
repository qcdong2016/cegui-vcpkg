


file(GLOB DEMO6_SOURCES ${CEGUI_ROOT_DIR}/Samples/Demo6/*.cpp)
file(GLOB DEMO6_HEADERS ${CEGUI_ROOT_DIR}/Samples/Demo6/*.h)


add_executable(Demo6 ${DEMO6_SOURCES} ${DEMO6_HEADERS})
set_library(Demo6)

target_include_directories(Demo6 PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(Demo6 PRIVATE CEGUISampleHelper)


set_target_properties(Demo6 PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
