
add_library(utility
    src/registers.cpp
)

add_library(laguna::utility ALIAS utility)

target_compile_definitions(utility
PRIVATE
)

target_include_directories(utility
PUBLIC
    $<INSTALL_INTERFACE:include>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/utility>
)

