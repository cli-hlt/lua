cmake_minimum_required( VERSION 2.8.12 )

project( lua C )

include_directories( src )

set( LUA_CORE_SRC src/lapi.c
                  src/lcode.c
                  src/lctype.c
                  src/ldebug.c
                  src/ldo.c
                  src/ldump.c
                  src/lfunc.c
                  src/lgc.c
                  src/llex.c
	                src/lmem.c
                  src/lobject.c
                  src/lopcodes.c
                  src/lparser.c
                  src/lstate.c
                  src/lstring.c
                  src/ltable.c
	                src/ltm.c
                  src/lundump.c
                  src/lvm.c
                  src/lzio.c)

set( LUA_LIB_SRC  src/lauxlib.c
                  src/lutf8lib.c
                  src/lbaselib.c
                  src/lbitlib.c
                  src/lcorolib.c
                  src/ldblib.c
                  src/liolib.c
	                src/lmathlib.c
                  src/loslib.c
                  src/lstrlib.c
                  src/ltablib.c
                  src/loadlib.c
                  src/linit.c)

set( LUA_HDR      src/lapi.h
                  src/lauxlib.h
                  src/lcode.h
                  src/lctype.h
                  src/ldebug.h
                  src/ldo.h
                  src/lfunc.h
                  src/lgc.h
                  src/llex.h
                  src/llimits.h
                  src/lmem.h
                  src/lobject.h
                  src/lopcodes.h
                  src/lparser.h
                  src/lstate.h
                  src/lstring.h
                  src/ltable.h
                  src/ltm.h
                  src/lua.h
                  src/luaconf.h
                  src/lualib.h
                  src/lundump.h
                  src/lvm.h
                  src/lzio.h
                  src/lprefix.h)

set( LUA_BINSRC   src/lua.c)
set( LUAC_BINSRC  src/luac.c)

add_definitions( -DLUA_COMPAT_ALL )

if( ${CMAKE_SYSTEM_NAME} STREQUAL Darwin )
  add_definitions( -DLUA_USE_MACOSX )

  find_library( READLINE_LIB readline )
  set( AUXLIB ${READLINE_LIB} )
elseif( ${CMAKE_SYSTEM_NAME} STREQUAL Linux )
  add_definitions( -DLUA_USE_LINUX )

  find_library( READLINE_LIB readline )
  set( AUXLIB "${READLINE_LIB} dl" )
endif()

add_library(lua STATIC ${LUA_CORE_SRC} ${LUA_LIB_SRC})

if( BUILD_LUA_BINARIES )
  add_executable( lua-bin ${LUA_BINSRC} )
  target_link_libraries( lua-bin lua ${AUXLIB} )
  set_target_properties( lua-bin PROPERTIES OUTPUT_NAME lua )

  add_executable( luac ${LUAC_BINSRC} )
  target_link_libraries( luac lua ${AUXLIB} )
endif()

if( ${${PROJECT_NAME}_SET_CMAKE_CACHE_VARIABLES} )
  set( ${PROJECT_NAME}_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/src
       CACHE INTERNAL "${PROJECT_NAME}: Include directories" FORCE )
  set( ${PROJECT_NAME}_LIBRARIES ${PROJECT_NAME}
       CACHE INTERNAL "${PROJECT_NAME}: Libraries" FORCE  )
endif()
