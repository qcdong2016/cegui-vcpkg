




file(GLOB CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/*.cpp)
file(GLOB CORE_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/*.h)
file(GLOB ELEMENTS_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/elements/*.cpp)
file(GLOB ELEMENTS_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/elements/*.h)
file(GLOB FALAGARD_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/falagard/*.cpp)
file(GLOB FALAGARD_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/falagard/*.h)


list(APPEND CORE_SOURCES ${ELEMENTS_SOURCES} ${FALAGARD_SOURCES})
list(APPEND CORE_HEADERS ${ELEMENTS_HEADERS} ${FALAGARD_HEADERS})


list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/minibidi.cpp)

if(NOT CEGUI_USE_DEFAULT_LOGGER)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIDefaultLogger.cpp)
endif()

if(NOT CEGUI_USE_FREETYPE)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIFreeTypeFont.cpp)
endif()

if(NOT CEGUI_USE_PCRE_REGEX)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIPCRERegexMatcher.cpp)
endif()

if(NOT CEGUI_BIDI_SUPPORT)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIFribidiVisualMapping.cpp)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIMinibidiVisualMapping.cpp)
else()
    if(CEGUI_USE_MINIBIDI)
        list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIFribidiVisualMapping.cpp)
    else()
        list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIMinibidiVisualMapping.cpp)
    endif()
endif()

if(NOT MINIZIP_RESOURCE_PROVIDER)
    list(REMOVE_ITEM CORE_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/CEGUIMinizipResourceProvider.cpp)
    list(REMOVE_ITEM CORE_HEADERS ${CEGUI_ROOT_DIR}/cegui/include/CEGUIMinizipResourceProvider.h)
else()
    file(GLOB MINIZIP_SOURCES ${CEGUI_ROOT_DIR}/cegui/src/minizip/*.cpp)
    file(GLOB MINIZIP_HEADERS ${CEGUI_ROOT_DIR}/cegui/src/minizip/*.h)
    list(APPEND CORE_SOURCES ${MINIZIP_SOURCES})
    list(APPEND CORE_HEADERS ${MINIZIP_HEADERS})
endif()



set(SRC_FILES ${CORE_SOURCES} ${CORE_HEADERS})

foreach(src_file ${SRC_FILES})
    get_filename_component(src_path ${src_file} PATH)
    get_filename_component(src_name ${src_file} NAME)

    
    string(REPLACE ${CEGUI_ROOT_DIR}/ "" relative_path ${src_path})
    string(REPLACE / \\ relative_path ${relative_path})

    
    if(src_path STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})
        set(relative_path "")
    endif()

    source_group("Source Files/${relative_path}" FILES ${src_file})
endforeach()

add_library(CEGUIBase STATIC ${SRC_FILES})
target_include_directories(CEGUIBase PUBLIC ${CEGUI_ROOT_DIR}/cegui/include/)

target_compile_definitions(CEGUIBase PUBLIC
-DCEGUI_STATIC
-DHAVE_CONFIG_H
)


if(CEGUI_USE_FREETYPE)
    find_package(Freetype REQUIRED)
    find_package(BZip2 REQUIRED)
    find_package(PNG REQUIRED)
    find_package(unofficial-brotli CONFIG REQUIRED)

    target_link_libraries(CEGUIBase PRIVATE Freetype::Freetype)
    target_link_libraries(CEGUIBase PRIVATE PNG::PNG)
    target_link_libraries(CEGUIBase PRIVATE BZip2::BZip2)
    target_link_libraries(CEGUIBase PRIVATE unofficial::brotli::brotlidec)
endif()

if(CEGUI_USE_PCRE_REGEX)
    
    find_package(unofficial-pcre CONFIG REQUIRED)
    
    target_link_libraries(CEGUIBase PRIVATE unofficial::pcre::pcre unofficial::pcre::pcre16 unofficial::pcre::pcre32 unofficial::pcre::pcrecpp)
endif()

if(CEGUI_BIDI_SUPPORT AND NOT CEGUI_USE_MINIBIDI)
    find_package(Fribidi REQUIRED)
    target_include_directories(CEGUIBase PRIVATE ${FRIBIDI_INCLUDE_DIRS})
    target_link_libraries(CEGUIBase PRIVATE ${FRIBIDI_LIBRARIES})
endif()


if(WIN32)
    target_link_libraries(CEGUIBase PRIVATE winmm)
endif()
set_library(CEGUIBase)