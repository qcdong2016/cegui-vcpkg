

file(GLOB LUA_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/ScriptingModules/LuaScriptModule/*.cpp)
file(GLOB LUA_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/ScriptingModules/LuaScriptModule/*.h)

add_library(CEGUILuaScriptModule SHARED ${LUA_SOURCES} ${LUA_HEADERS})


target_link_libraries(CEGUILuaScriptModule PRIVATE CEGUIBase)


find_package(Lua REQUIRED)
target_include_directories(CEGUILuaScriptModule PRIVATE ${LUA_INCLUDE_DIRS})
target_link_libraries(CEGUILuaScriptModule PRIVATE ${LUA_LIBRARIES})


add_subdirectory(support/tolua++)
add_subdirectory(support/tolua++bin)
