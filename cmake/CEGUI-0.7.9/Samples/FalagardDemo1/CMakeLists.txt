


file(GLOB FALAGARD_DEMO1_SOURCES ${CEGUI_ROOT_DIR}/Samples/FalagardDemo1/*.cpp)
file(GLOB FALAGARD_DEMO1_HEADERS ${CEGUI_ROOT_DIR}/Samples/FalagardDemo1/*.h)


add_executable(FalagardDemo1 ${FALAGARD_DEMO1_SOURCES} ${FALAGARD_DEMO1_HEADERS})
set_library(FalagardDemo1)

target_include_directories(FalagardDemo1 PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(FalagardDemo1 PRIVATE CEGUISampleHelper)


set_target_properties(FalagardDemo1 PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
