cmake_minimum_required(VERSION 2.8)
set(_ECLIPSE_VERSION 4.5)
project(libdict)

enable_language(C)
add_definitions(-std=c99)

set(LIBDICT_SOURCES
    src/dict.c
    src/hashtable2.c
    src/hb_tree.c
    src/rb_tree.c
    src/sp_tree.c
    src/tree_common.c
    src/hashtable.c
    src/hashtable_common.c
    src/pr_tree.c
    src/skiplist.c
    src/tr_tree.c
    src/wb_tree.c
)

include_directories(include)
include_directories(src)

add_library(dict STATIC ${LIBDICT_SOURCES})
if(CMAKE_SYSTEM_PROCESSOR STREQUAL "x86_64" )
    set_target_properties(dict PROPERTIES COMPILE_FLAGS "-fPIC")
endif(CMAKE_SYSTEM_PROCESSOR STREQUAL "x86_64" )
set_target_properties(dict PROPERTIES PREFIX "lib")


