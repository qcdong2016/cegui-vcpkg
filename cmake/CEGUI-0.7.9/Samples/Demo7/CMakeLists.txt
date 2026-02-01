


file(GLOB DEMO7_SOURCES ${CEGUI_ROOT_DIR}/Samples/Demo7/*.cpp)
file(GLOB DEMO7_HEADERS ${CEGUI_ROOT_DIR}/Samples/Demo7/*.h)


add_executable(Demo7 ${DEMO7_SOURCES} ${DEMO7_HEADERS})
set_library(Demo7)

target_include_directories(Demo7 PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(Demo7 PRIVATE CEGUISampleHelper)


set_target_properties(Demo7 PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
