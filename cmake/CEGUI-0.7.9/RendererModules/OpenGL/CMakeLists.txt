
find_package(GLEW CONFIG REQUIRED)
  
file(GLOB OPENGL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/OpenGL/*.cpp)
file(GLOB OPENGL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/OpenGL/*.h)


if(WIN32)
    list(REMOVE_ITEM OPENGL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/OpenGL/CEGUIOpenGLGLXPBTextureTarget.cpp)
    list(REMOVE_ITEM OPENGL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/OpenGL/CEGUIOpenGLGLXPBTextureTarget.h)
    list(REMOVE_ITEM OPENGL_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/OpenGL/CEGUIOpenGLApplePBTextureTarget.cpp)
    list(REMOVE_ITEM OPENGL_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/RendererModules/OpenGL/CEGUIOpenGLApplePBTextureTarget.h)
endif()

add_library(CEGUIOpenGLRenderer STATIC ${OPENGL_SOURCES} ${OPENGL_HEADERS} ${GLEW_SOURCES} ${GLEW_HEADERS})
target_include_directories(CEGUIOpenGLRenderer PUBLIC 
${CEGUI_ROOT_DIR}/cegui/include/RendererModules/OpenGL/)

set_library(CEGUIOpenGLRenderer)


target_compile_definitions(CEGUIOpenGLRenderer PRIVATE -DOPENGL_GUIRENDERER_EXPORTS -DGLEW_STATIC)


target_include_directories(CEGUIOpenGLRenderer PRIVATE ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/OpenGL)
target_include_directories(CEGUIOpenGLRenderer PRIVATE ${CEGUI_ROOT_DIR}/cegui/src/RendererModules/OpenGL/GLEW)


target_link_libraries(CEGUIOpenGLRenderer PRIVATE CEGUIBase GLEW::GLEW)


if(WIN32)
    target_link_libraries(CEGUIOpenGLRenderer PRIVATE glu32 opengl32)
    target_compile_definitions(CEGUIOpenGLRenderer PRIVATE -DNOMINMAX)
elseif(UNIX)
    find_package(OpenGL REQUIRED)
    find_package(GLU REQUIRED)
    target_link_libraries(CEGUIOpenGLRenderer PRIVATE ${OPENGL_LIBRARIES} ${GLU_LIBRARIES})
endif()