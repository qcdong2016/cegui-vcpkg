


file(GLOB MINESWEEPER_SOURCES ${CEGUI_ROOT_DIR}/Samples/Minesweeper/*.cpp)
file(GLOB MINESWEEPER_HEADERS ${CEGUI_ROOT_DIR}/Samples/Minesweeper/*.h)


add_executable(Minesweeper ${MINESWEEPER_SOURCES} ${MINESWEEPER_HEADERS})
set_library(Minesweeper)

target_include_directories(Minesweeper PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(Minesweeper PRIVATE CEGUISampleHelper)


set_target_properties(Minesweeper PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
