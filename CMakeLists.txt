cmake_minimum_required(VERSION 3.7)
project(Filters)

include(filters.cmake)

add_definitions(-fpic)

SET(LIBFAAD_SRC
        ${CMAKE_CURRENT_SOURCE_DIR}/dec_faad.c
        ${CMAKE_CURRENT_SOURCE_DIR}/reframe_adts.c
        ${CMAKE_CURRENT_SOURCE_DIR}/reframe_mp3.c
        ${CMAKE_CURRENT_SOURCE_DIR}/av_parsers.c
        ${CMAKE_CURRENT_SOURCE_DIR}/bitstream.c
)

SET(LIBFAAD_LIB
        ${CMAKE_CURRENT_SOURCE_DIR}/lib/libfaad.a
)

SET(LIBFAAD_INC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

add_filter(libfaad
        "${LIBFAAD_SRC}"
        "${LIBFAAD_LIB}"
        []
        GPAC_HAS_FAAD
        "${LIBFAAD_INC}"
        ""
        "1")
