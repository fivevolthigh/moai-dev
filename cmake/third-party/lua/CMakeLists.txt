cmake_minimum_required(VERSION 2.8.5)

project(lua)

set ( CMAKE_CURRENT_SOURCE_DIR "${MOAI_ROOT}/3rdparty/lua-5.1.3/src/" )

set ( LUA_INCLUDES "${MOAI_ROOT}/3rdparty/lua-5.1.3/src/"  )


set ( LUA_SOURCES
  ${CMAKE_CURRENT_SOURCE_DIR}lapi.c
  ${CMAKE_CURRENT_SOURCE_DIR}lauxlib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lbaselib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lcode.c
  ${CMAKE_CURRENT_SOURCE_DIR}ldblib.c
  ${CMAKE_CURRENT_SOURCE_DIR}ldebug.c
  ${CMAKE_CURRENT_SOURCE_DIR}ldo.c
  ${CMAKE_CURRENT_SOURCE_DIR}ldump.c
  ${CMAKE_CURRENT_SOURCE_DIR}lfunc.c
  ${CMAKE_CURRENT_SOURCE_DIR}lgc.c
  ${CMAKE_CURRENT_SOURCE_DIR}linit.c
  ${CMAKE_CURRENT_SOURCE_DIR}liolib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lmathlib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lmem.c
  ${CMAKE_CURRENT_SOURCE_DIR}loadlib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lobject.c
  ${CMAKE_CURRENT_SOURCE_DIR}lopcodes.c
  ${CMAKE_CURRENT_SOURCE_DIR}loslib.c
  ${CMAKE_CURRENT_SOURCE_DIR}lparser.c
  ${CMAKE_CURRENT_SOURCE_DIR}lstate.c
  ${CMAKE_CURRENT_SOURCE_DIR}lstring.c
  ${CMAKE_CURRENT_SOURCE_DIR}lstrlib.c
  ${CMAKE_CURRENT_SOURCE_DIR}ltable.c
  ${CMAKE_CURRENT_SOURCE_DIR}ltablib.c
  ${CMAKE_CURRENT_SOURCE_DIR}ltm.c
  ${CMAKE_CURRENT_SOURCE_DIR}lundump.c
  ${CMAKE_CURRENT_SOURCE_DIR}lvm.c
  ${CMAKE_CURRENT_SOURCE_DIR}lzio.c
  ${CMAKE_CURRENT_SOURCE_DIR}print.c
)
 
if (BUILD_ANDROID)
  set ( LUA_SOURCES 
    ${LUA_SOURCES} 
    ${CMAKE_CURRENT_SOURCE_DIR}/android/llex.c 
  )
else (BUILD_ANDROID) 
	set ( LUA_SOURCES 
    ${LUA_SOURCES} 
    ${CMAKE_CURRENT_SOURCE_DIR}/llex.c 
  )
endif (BUILD_ANDROID)

add_library( liblua-static STATIC ${LUA_SOURCES} )
target_include_directories( liblua-static PUBLIC ${LUA_INCLUDES} )
set (LUA_HEADERS ${LUA_INCLUDES} PARENT_SCOPE)
set (LUA_LIB liblua-static PARENT_SCOPE)
set_target_properties( liblua-static PROPERTIES FOLDER Third-Party )

