


file(GLOB INVENTORY_DEMO_SOURCES ${CEGUI_ROOT_DIR}/Samples/InventoryDemo/*.cpp)
file(GLOB INVENTORY_DEMO_HEADERS ${CEGUI_ROOT_DIR}/Samples/InventoryDemo/*.h)


add_executable(InventoryDemo ${INVENTORY_DEMO_SOURCES} ${INVENTORY_DEMO_HEADERS})
set_library(InventoryDemo)

target_include_directories(InventoryDemo PRIVATE
    ${CEGUI_ROOT_DIR}/Samples/common/include
    ${CEGUI_ROOT_DIR}/cegui/include
)


target_link_libraries(InventoryDemo PRIVATE CEGUISampleHelper)


set_target_properties(InventoryDemo PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
