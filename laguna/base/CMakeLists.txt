
add_library(base
    src/dev_ctrl.cpp
)

add_library(laguna::base ALIAS base)

target_compile_definitions(base
PRIVATE
)

target_include_directories(base
PUBLIC
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/base>
)

