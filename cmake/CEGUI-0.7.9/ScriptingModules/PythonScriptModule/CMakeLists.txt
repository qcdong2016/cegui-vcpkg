


add_subdirectory(PyCEGUI)


if(OPENGL_RENDERER)
    add_subdirectory(PyCEGUIOpenGLRenderer)
endif()

if(NULL_RENDERER)
    add_subdirectory(PyCEGUINullRenderer)
endif()

if(OGRE_RENDERER)
    add_subdirectory(PyCEGUIOgreRenderer)
endif()
