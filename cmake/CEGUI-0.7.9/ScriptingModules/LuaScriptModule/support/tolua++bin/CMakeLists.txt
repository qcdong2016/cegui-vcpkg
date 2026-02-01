

file(GLOB TOLUA_BIN_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/LuaScriptModule/support/tolua++bin/*.cpp)

add_executable(tolua++bin ${TOLUA_BIN_SOURCES})


target_link_libraries(tolua++bin PRIVATE tolua++)
