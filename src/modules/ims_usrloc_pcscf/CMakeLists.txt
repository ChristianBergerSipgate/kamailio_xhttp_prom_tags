file(GLOB SRC_FILES "*.c")

add_library(ims_usrloc_pcscf SHARED ${SRC_FILES})

# target_link_libraries(.*PRIVATE)

target_compile_options(ims_usrloc_pcscf PUBLIC "-ffile-prefix-map=${CMAKE_SOURCE_DIR}/src/modules/ims_usrloc_pcscf/=")
