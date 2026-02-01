

file(GLOB TOLUA_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/LuaScriptModule/support/tolua++/*.cpp)
file(GLOB TOLUA_HEADERS ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/LuaScriptModule/support/tolua++/*.h)

add_library(tolua++ STATIC ${TOLUA_SOURCES} ${TOLUA_HEADERS})


find_package(Lua REQUIRED)
target_include_directories(tolua++ PRIVATE ${LUA_INCLUDE_DIRS})
target_link_libraries(tolua++ PRIVATE ${LUA_LIBRARIES})
