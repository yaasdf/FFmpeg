if (${BUILD_X64})
    set(FFMPEG_LIB_PATH ${CMAKE_CURRENT_LIST_DIR}/lib/x64)
else()
    set(FFMPEG_LIB_PATH ${CMAKE_CURRENT_LIST_DIR}/lib/x86)
endif()

if (WIN32)
    set(FFMPEG_LIB_FILES 
        ${FFMPEG_LIB_PATH}/avcodec-59.dll
        ${FFMPEG_LIB_PATH}/avdevice-59.dll
        ${FFMPEG_LIB_PATH}/avfilter-8.dll
        ${FFMPEG_LIB_PATH}/avformat-59.dll
        ${FFMPEG_LIB_PATH}/swresample-4.dll
        ${FFMPEG_LIB_PATH}/avutil-57.dll
        ${FFMPEG_LIB_PATH}/swscale-6.dll
        ${FFMPEG_LIB_PATH}/libwinpthread-1.dll
        )
    set(FFMPEG_IMPORT_LIBS
        ${FFMPEG_LIB_PATH}/avcodec.lib
        ${FFMPEG_LIB_PATH}/avdevice.lib
        ${FFMPEG_LIB_PATH}/avfilter.lib
        ${FFMPEG_LIB_PATH}/avformat.lib
        ${FFMPEG_LIB_PATH}/swresample.lib
        ${FFMPEG_LIB_PATH}/avutil.lib
        ${FFMPEG_LIB_PATH}/swscale.lib
        )
else ()
    set(FFMPEG_LIB_FILES )
    set(FFMPEG_IMPORT_LIBS )
endif()

add_library(libavcodec    SHARED IMPORTED GLOBAL)
add_library(libavdevice   SHARED IMPORTED GLOBAL)
add_library(libavfilter   SHARED IMPORTED GLOBAL)
add_library(libavformat   SHARED IMPORTED GLOBAL)
add_library(libswresample SHARED IMPORTED GLOBAL)
add_library(libavutil     SHARED IMPORTED GLOBAL)
add_library(libswscale    SHARED IMPORTED GLOBAL)
target_include_directories(libavcodec    INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libavdevice   INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libavfilter   INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libavformat   INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libswresample INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libavutil     INTERFACE ${CMAKE_CURRENT_LIST_DIR})
target_include_directories(libswscale    INTERFACE ${CMAKE_CURRENT_LIST_DIR})
    
if (WIN32)
    set_target_properties(libavcodec PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/avcodec-59.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/avcodec.lib
    )
    set_target_properties(libavdevice PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/avdevice-59.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/avdevice.lib
    )
    set_target_properties(libavfilter PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/avfilter-8.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/avfilter.lib
    )
    set_target_properties(libavformat PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/avformat-59.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/avformat.lib
    )
    set_target_properties(libswresample PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/swresample-4.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/swresample.lib
    )
    set_target_properties(libavutil PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/avutil-57.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/avutil.lib
    )
    set_target_properties(libswscale PROPERTIES
        IMPORTED_LOCATION   ${FFMPEG_LIB_PATH}/swscale-6.dll
        IMPORTED_IMPLIB     ${FFMPEG_LIB_PATH}/swscale.lib
    )
elseif (LINUX)

endif()

set(EXT_DEPEND_LIBFILES ${EXT_DEPEND_LIBFILES} 
        ${FFMPEG_LIB_FILES}
        CACHE INTERNAL "dependencies"
)
set(EXT_DEPEND_LIBFILES_SET TRUE CACHE INTERNAL "dependencies")
