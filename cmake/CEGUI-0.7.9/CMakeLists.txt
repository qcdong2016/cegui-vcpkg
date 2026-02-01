cmake_minimum_required(VERSION 3.20)
project(CEGUI)

set(CEGUI_VERSION 0.7.9)


if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Build type" FORCE)
endif()

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)


option(WANT_RELEASE_WITH_SYMBOLS_BUILD "Build ReleaseWithSymbols configuration" ON)
option(WANT_STATIC_BUILD "Build static libraries" ON)
option(STATIC_BUILD_WITH_DYNAMIC_DEPS "Use dynamic dependencies for static build" OFF)
option(FULLY_CHECKED_DEBUG_ITERATORS "Enable fully checked debug iterators" ON)


set(IRRLICHT_PATHS "irrlicht-1.7.1" "include" "lib/Win32-visualstudio" CACHE STRING "Irrlicht SDK paths")
set(OGRE_PATHS "C:/OgreSDK" "include" "lib" CACHE STRING "Ogre SDK paths")
set(OIS_PATHS "C:/OgreSDK" "include/OIS" "lib" CACHE STRING "OIS SDK paths")
set(RAPIDXML_PATHS "rapidxml-1.13" "" "" CACHE STRING "RapidXML paths")
set(PYTHON_PATHS "C:/Python26" "include" "libs" CACHE STRING "Python paths")
set(BOOST_PYTHON_PATHS "C:/Program Files/boost/boost_1_44" "" "lib" CACHE STRING "Boost Python paths")


set(CEGUI_EXTRA_PATHS "" CACHE STRING "Extra dependency paths")


set(CEGUI_IRR_SDK_VERSION 16 CACHE STRING "Irrlicht SDK version")
option(CEGUI_OLD_OIS_API "Use older OIS API" OFF)
set(LUA_VERSION 51 CACHE STRING "Lua version")

option(CEGUI_USE_FREETYPE "Use FreeType library for font support" ON)
option(CEGUI_USE_PCRE_REGEX "Use PCRE library for regex support" ON)
option(CEGUI_USE_DEFAULT_LOGGER "Build CEGUI::DefaultLogger" ON)
option(CEGUI_BIDI_SUPPORT "Enable bidirectional text support" OFF)
option(CEGUI_USE_MINIBIDI "Use minibidi for BIDI support" ON)
option(MINIZIP_RESOURCE_PROVIDER "Build MinizipResourceProvider" OFF)


option(OPENGL_RENDERER "Build OpenGL renderer" ON)
option(DIRECT3D9_RENDERER "Build Direct3D9 renderer" OFF)
option(DIRECT3D10_RENDERER "Build Direct3D10 renderer" OFF)
option(DIRECT3D11_RENDERER "Build Direct3D11 renderer" OFF)
option(IRRLICHT_RENDERER "Build Irrlicht renderer" OFF)
option(OGRE_RENDERER "Build Ogre renderer" OFF)
option(NULL_RENDERER "Build Null renderer" OFF)

option(TGA_IMAGE_CODEC "Build TGA image codec" OFF)
option(SILLY_IMAGE_CODEC "Build SILLY image codec" OFF)
option(DEVIL_IMAGE_CODEC "Build DevIL image codec" OFF)
option(FREEIMAGE_IMAGE_CODEC "Build FreeImage image codec" OFF)
option(CORONA_IMAGE_CODEC "Build Corona image codec" OFF)
option(STB_IMAGE_CODEC "Build STB image codec" ON)

set(DEFAULT_IMAGE_CODEC "silly" CACHE STRING "Default image codec")
set_property(CACHE DEFAULT_IMAGE_CODEC PROPERTY STRINGS tga silly devil freeimage corona stb)


option(FALAGARD_WR "Build Falagard window renderer" ON)
set(DEFAULT_WINDOW_RENDERER "falagard" CACHE STRING "Default window renderer")
set_property(CACHE DEFAULT_WINDOW_RENDERER PROPERTY STRINGS falagard)


option(EXPAT_PARSER "Build Expat XML parser" ON)
option(XERCES_PARSER "Build Xerces XML parser" OFF)
option(TINYXML_PARSER "Build TinyXML parser" OFF)
option(RAPIDXML_PARSER "Build RapidXML parser" OFF)
option(LIBXML_PARSER "Build Libxml parser" OFF)

set(DEFAULT_XML_PARSER "expat" CACHE STRING "Default XML parser")
set_property(CACHE DEFAULT_XML_PARSER PROPERTY STRINGS expat xerces tinyxml rapidxml libxml)


option(LUA_SCRIPT_MODULE "Build Lua script module" OFF)
option(LUA_SCRIPT_MODULE_SAFE "Enable safe mode for Lua module" OFF)
option(TOLUA_STATIC "Build bundled tolua++ as static library" OFF)
option(PYTHON_EXTENSION_MODULE "Build Python extension modules" OFF)


option(SAMPLES_INCLUDED "Include samples in build" ON)
option(SAMPLES_GL "Build OpenGL samples" ON)
option(SAMPLES_DX9 "Build Direct3D9 samples" OFF)
option(SAMPLES_DX10 "Build Direct3D10 samples" OFF)
option(SAMPLES_IRRLICHT "Build Irrlicht samples" OFF)
option(SAMPLES_OGRE "Build Ogre samples" OFF)


macro (set_library name)
    set_target_properties(${name} PROPERTIES 
    MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
    )
endmacro()


include_directories(${CEGUI_ROOT_DIR}/cegui/include)
include_directories(${CMAKE_BINARY_DIR}/cegui/include)




if(DEFAULT_XML_PARSER STREQUAL "expat")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_EXPAT")
elseif(DEFAULT_XML_PARSER STREQUAL "xerces")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_XERCES")
elseif(DEFAULT_XML_PARSER STREQUAL "tinyxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_TINYXML")
elseif(DEFAULT_XML_PARSER STREQUAL "rapidxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_RAPIDXML")
elseif(DEFAULT_XML_PARSER STREQUAL "libxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_LIBXML")
endif()


if(DEFAULT_IMAGE_CODEC STREQUAL "silly")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_SILLY")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "tga")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_TGA")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "devil")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_DEVIL")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "freeimage")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_FREEIMAGE")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "corona")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_CORONA")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "stb")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_STB")
endif()


if(SAMPLES_GL)
    set(CEGUI_SAMPLES_USE_OPENGL "#define CEGUI_SAMPLES_USE_OPENGL")
endif()

if(SAMPLES_DX9)
    set(CEGUI_SAMPLES_USE_DIRECTX_9 "#define CEGUI_SAMPLES_USE_DIRECTX_9")
endif()

if(SAMPLES_DX10)
    set(CEGUI_SAMPLES_USE_DIRECTX_10 "#define CEGUI_SAMPLES_USE_DIRECTX_10")
endif()

if(SAMPLES_OGRE)
    set(CEGUI_SAMPLES_USE_OGRE "#define CEGUI_SAMPLES_USE_OGRE")
endif()

if(SAMPLES_IRRLICHT)
    set(CEGUI_SAMPLES_USE_IRRLICHT "#define CEGUI_SAMPLES_USE_IRRLICHT")
    set(CEGUI_IRR_SDK_VERSION "#define CEGUI_IRR_SDK_VERSION ${CEGUI_IRR_SDK_VERSION}")
endif()


if(EXPAT_PARSER)
    set(CEGUI_WITH_EXPAT "#define CEGUI_WITH_EXPAT")
endif()

if(XERCES_PARSER)
    set(CEGUI_WITH_XERCES "#define CEGUI_WITH_XERCES")
endif()

if(TINYXML_PARSER)
    set(CEGUI_WITH_TINYXML "#define CEGUI_WITH_TINYXML")
endif()


if(SILLY_IMAGE_CODEC)
    set(CEGUI_CODEC_SILLY "#define CEGUI_CODEC_SILLY")
endif()

if(TGA_IMAGE_CODEC)
    set(CEGUI_CODEC_TGA "#define CEGUI_CODEC_TGA")
endif()

if(CORONA_IMAGE_CODEC)
    set(CEGUI_CODEC_CORONA "#define CEGUI_CODEC_CORONA")
endif()

if(DEVIL_IMAGE_CODEC)
    set(CEGUI_CODEC_DEVIL "#define CEGUI_CODEC_DEVIL")
endif()

if(FREEIMAGE_IMAGE_CODEC)
    set(CEGUI_CODEC_FREEIMAGE "#define CEGUI_CODEC_FREEIMAGE")
endif()

if(STB_IMAGE_CODEC)
    set(CEGUI_CODEC_STB "#define CEGUI_CODEC_STB")
endif()


set(CEGUI_LUA_VER "#define CEGUI_LUA_VER ${LUA_VERSION}")


if(FALAGARD_WR)
    set(CEGUI_FALAGARD_RENDERER "#define CEGUI_FALAGARD_RENDERER")
endif()


if(CEGUI_USE_FREETYPE)
    set(CEGUI_HAS_FREETYPE "#define CEGUI_HAS_FREETYPE")
endif()

if(CEGUI_USE_PCRE_REGEX)
    set(CEGUI_HAS_PCRE_REGEX "#define CEGUI_HAS_PCRE_REGEX")
endif()

if(CEGUI_USE_DEFAULT_LOGGER)
    set(CEGUI_HAS_DEFAULT_LOGGER "#define CEGUI_HAS_DEFAULT_LOGGER")
endif()


if(CEGUI_BIDI_SUPPORT)
    set(CEGUI_BIDI_SUPPORT "#define CEGUI_BIDI_SUPPORT")
    if(CEGUI_USE_MINIBIDI)
        set(CEGUI_USE_MINIBIDI "#define CEGUI_USE_MINIBIDI")
    else()
        set(CEGUI_USE_FRIBIDI "#define CEGUI_USE_FRIBIDI")
    endif()
endif()


if(MINIZIP_RESOURCE_PROVIDER)
    set(CEGUI_HAS_MINIZIP_RESOURCE_PROVIDER "#define CEGUI_HAS_MINIZIP_RESOURCE_PROVIDER")
endif()


set(CEGUI_DEFAULT_XMLPARSER "")
set(CEGUI_DEFAULT_IMAGE_CODEC "")
set(CEGUI_SAMPLES_USE_OPENGL "")
set(CEGUI_SAMPLES_USE_DIRECTX_9 "")
set(CEGUI_SAMPLES_USE_DIRECTX_10 "")
set(CEGUI_SAMPLES_USE_OGRE "")
set(CEGUI_SAMPLES_USE_IRRLICHT "")
set(CEGUI_IRR_SDK_VERSION "")
set(CEGUI_WITH_XERCES "")
set(CEGUI_WITH_EXPAT "")
set(CEGUI_WITH_TINYXML "")
set(CEGUI_CODEC_SILLY "")
set(CEGUI_CODEC_TGA "")
set(CEGUI_CODEC_CORONA "")
set(CEGUI_CODEC_DEVIL "")
set(CEGUI_CODEC_FREEIMAGE "")
set(CEGUI_CODEC_STB "")
set(CEGUI_LUA_VER "")
set(CEGUI_FALAGARD_RENDERER "")
set(CEGUI_HAS_FREETYPE "")
set(CEGUI_HAS_PCRE_REGEX "")
set(CEGUI_HAS_DEFAULT_LOGGER "")
set(CEGUI_BIDI_SUPPORT "")
set(CEGUI_USE_MINIBIDI "")
set(CEGUI_USE_FRIBIDI "")
set(CEGUI_HAS_MINIZIP_RESOURCE_PROVIDER "")




if(DEFAULT_XML_PARSER STREQUAL "expat")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_EXPAT")
elseif(DEFAULT_XML_PARSER STREQUAL "xerces")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_XERCES")
elseif(DEFAULT_XML_PARSER STREQUAL "tinyxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_TINYXML")
elseif(DEFAULT_XML_PARSER STREQUAL "rapidxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_RAPIDXML")
elseif(DEFAULT_XML_PARSER STREQUAL "libxml")
    set(CEGUI_DEFAULT_XMLPARSER "#define CEGUI_DEFAULT_XMLPARSER_LIBXML")
endif()


if(DEFAULT_IMAGE_CODEC STREQUAL "silly")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_SILLY")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "tga")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_TGA")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "devil")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_DEVIL")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "freeimage")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_FREEIMAGE")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "corona")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_CORONA")
elseif(DEFAULT_IMAGE_CODEC STREQUAL "stb")
    set(CEGUI_DEFAULT_IMAGE_CODEC "#define CEGUI_DEFAULT_IMAGE_CODEC_STB")
endif()


if(SAMPLES_GL)
    set(CEGUI_SAMPLES_USE_OPENGL "#define CEGUI_SAMPLES_USE_OPENGL")
endif()

if(SAMPLES_DX9)
    set(CEGUI_SAMPLES_USE_DIRECTX_9 "#define CEGUI_SAMPLES_USE_DIRECTX_9")
endif()

if(SAMPLES_DX10)
    set(CEGUI_SAMPLES_USE_DIRECTX_10 "#define CEGUI_SAMPLES_USE_DIRECTX_10")
endif()

if(SAMPLES_OGRE)
    set(CEGUI_SAMPLES_USE_OGRE "#define CEGUI_SAMPLES_USE_OGRE")
endif()

if(SAMPLES_IRRLICHT)
    set(CEGUI_SAMPLES_USE_IRRLICHT "#define CEGUI_SAMPLES_USE_IRRLICHT")
    set(CEGUI_IRR_SDK_VERSION "#define CEGUI_IRR_SDK_VERSION ${CEGUI_IRR_SDK_VERSION}")
endif()


if(EXPAT_PARSER)
    set(CEGUI_WITH_EXPAT "#define CEGUI_WITH_EXPAT")
endif()

if(XERCES_PARSER)
    set(CEGUI_WITH_XERCES "#define CEGUI_WITH_XERCES")
endif()

if(TINYXML_PARSER)
    set(CEGUI_WITH_TINYXML "#define CEGUI_WITH_TINYXML")
endif()


if(SILLY_IMAGE_CODEC)
    set(CEGUI_CODEC_SILLY "#define CEGUI_CODEC_SILLY")
endif()

if(TGA_IMAGE_CODEC)
    set(CEGUI_CODEC_TGA "#define CEGUI_CODEC_TGA")
endif()

if(CORONA_IMAGE_CODEC)
    set(CEGUI_CODEC_CORONA "#define CEGUI_CODEC_CORONA")
endif()

if(DEVIL_IMAGE_CODEC)
    set(CEGUI_CODEC_DEVIL "#define CEGUI_CODEC_DEVIL")
endif()

if(FREEIMAGE_IMAGE_CODEC)
    set(CEGUI_CODEC_FREEIMAGE "#define CEGUI_CODEC_FREEIMAGE")
endif()

if(STB_IMAGE_CODEC)
    set(CEGUI_CODEC_STB "#define CEGUI_CODEC_STB")
endif()


set(CEGUI_LUA_VER "#define CEGUI_LUA_VER ${CEGUI_LUA_VER}")


if(FALAGARD_WR)
    set(CEGUI_FALAGARD_RENDERER "#define CEGUI_FALAGARD_RENDERER")
endif()


if(CEGUI_USE_FREETYPE)
    set(CEGUI_HAS_FREETYPE "#define CEGUI_HAS_FREETYPE")
endif()

if(CEGUI_USE_PCRE_REGEX)
    set(CEGUI_HAS_PCRE_REGEX "#define CEGUI_HAS_PCRE_REGEX")
endif()

if(CEGUI_USE_DEFAULT_LOGGER)
    set(CEGUI_HAS_DEFAULT_LOGGER "#define CEGUI_HAS_DEFAULT_LOGGER")
endif()


if(CEGUI_BIDI_SUPPORT)
    set(CEGUI_BIDI_SUPPORT "#define CEGUI_BIDI_SUPPORT")
    if(CEGUI_USE_MINIBIDI)
        set(CEGUI_USE_MINIBIDI "#define CEGUI_USE_MINIBIDI")
    else()
        set(CEGUI_USE_FRIBIDI "#define CEGUI_USE_FRIBIDI")
    endif()
endif()


if(MINIZIP_RESOURCE_PROVIDER)
    set(CEGUI_HAS_MINIZIP_RESOURCE_PROVIDER "#define CEGUI_HAS_MINIZIP_RESOURCE_PROVIDER")
endif()


configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/config.h.cmake.in
    ${CMAKE_BINARY_DIR}/cegui/include/config.h
    @ONLY
)


add_subdirectory(BaseSystem)


if(FALAGARD_WR)
    add_subdirectory(WindowRendererSets/Falagard)
endif()


if(OPENGL_RENDERER)
    add_subdirectory(RendererModules/OpenGL)
endif()

if(DIRECT3D9_RENDERER)
    add_subdirectory(RendererModules/Direct3D9)
endif()

if(DIRECT3D10_RENDERER)
    add_subdirectory(RendererModules/Direct3D10)
endif()

if(DIRECT3D11_RENDERER)
    add_subdirectory(RendererModules/Direct3D11)
endif()

if(IRRLICHT_RENDERER)
    add_subdirectory(RendererModules/Irrlicht)
endif()

if(OGRE_RENDERER)
    add_subdirectory(RendererModules/Ogre)
endif()

if(NULL_RENDERER)
    add_subdirectory(RendererModules/Null)
endif()


if(TGA_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/TGAImageCodec)
endif()

if(SILLY_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/SILLYImageCodec)
endif()

if(DEVIL_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/DevILImageCodec)
endif()

if(FREEIMAGE_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/FreeImageImageCodec)
endif()

if(CORONA_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/CoronaImageCodec)
endif()

if(STB_IMAGE_CODEC)
    add_subdirectory(ImageCodecModules/STBImageCodec)
endif()


if(EXPAT_PARSER)
    add_subdirectory(XMLParserModules/expatParser)
endif()

if(XERCES_PARSER)
    add_subdirectory(XMLParserModules/XercesParser)
endif()

if(TINYXML_PARSER)
    add_subdirectory(XMLParserModules/TinyXMLParser)
endif()

if(RAPIDXML_PARSER)
    add_subdirectory(XMLParserModules/RapidXMLParser)
endif()

if(LIBXML_PARSER)
    add_subdirectory(XMLParserModules/libxmlParser)
endif()


if(LUA_SCRIPT_MODULE)
    add_subdirectory(ScriptingModules/LuaScriptModule)
endif()

if(PYTHON_EXTENSION_MODULE)
    add_subdirectory(ScriptingModules/PythonScriptModule)
endif()


if(SAMPLES_INCLUDED)
    add_subdirectory(Samples)
endif()