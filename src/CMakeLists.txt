if(NATIVEBRIDGE STREQUAL "houdini")
    set(INCLUDED_PATCH_SOURCE "houdini_${NB_VERSION}_patches.cpp")
elseif(NATIVEBRIDGE STREQUAL "ndk_translation")
    if(NB_VERSION STREQUAL "R112")
        set(INCLUDED_PATCH_SOURCE "ndk_translation_R112-15359.58.0_patches.cpp")
    elseif(NB_VERSION STREQUAL "R125")
        set(INCLUDED_PATCH_SOURCE "ndk_translation_R125-15853.53.0_patches.cpp")
    else()
        message(FATAL_ERROR "Unsupported ndk_translation version: ${NB_VERSION}")
    endif()
else()
    message(FATAL_ERROR "Unknown native bridge: ${NATIVEBRIDGE}")
endif()

message(STATUS "Using patch source: ${INCLUDED_PATCH_SOURCE}")

add_library(nb SHARED main.cpp ${INCLUDED_PATCH_SOURCE})

target_link_libraries(nb log)
