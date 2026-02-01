


add_subdirectory(common)


set(SAMPLE_PROJECTS
    Demo6
    Demo7
    DragDropDemo
    FalagardDemo1
    FirstWindow
    FontDemo
    InventoryDemo
    Minesweeper
    ScrollablePaneDemo
    TabControlDemo
    TextDemo
    TreeDemo
)


foreach(SAMPLE ${SAMPLE_PROJECTS})
    add_subdirectory(${SAMPLE})
endforeach()

if (LUA_SCRIPT_MODULE)
    add_subdirectory(Demo8)
endif()