find_package(PkgConfig REQUIRED)
pkg_check_modules(nats REQUIRED IMPORTED_TARGET libnats)
add_library(nats::libnats ALIAS PkgConfig::nats)
pkg_check_modules(uv REQUIRED IMPORTED_TARGET libuv)
add_library(uv::libuv ALIAS PkgConfig::uv)

file(GLOB SRC_FILES "*.c")

add_library(nats SHARED ${SRC_FILES})
target_link_libraries(nats PRIVATE nats::libnats uv::libuv)

target_compile_options(nats PUBLIC "-ffile-prefix-map=${CMAKE_SOURCE_DIR}/src/modules/nats/=")
