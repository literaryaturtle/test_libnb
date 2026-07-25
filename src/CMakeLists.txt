set(INCLUDED_PATCH_SOURCE "ndk_translation_R112-15359.58.0_patches.cpp")

message(STATUS "Using patch source: ${INCLUDED_PATCH_SOURCE}")

add_library(nb SHARED main.cpp ${INCLUDED_PATCH_SOURCE})

target_link_libraries(nb log)
