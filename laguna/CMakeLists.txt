cmake_minimum_required(VERSION 3.13)

project(laguna-prj VERSION 1.0.0 LANGUAGES CXX C)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_subdirectory(base)
add_subdirectory(utility)

##############################################
# Installation instructions

include(GNUInstallDirs)
set(INSTALL_CONFIGDIR ${CMAKE_INSTALL_LIBDIR}/cmake/laguna)

install(TARGETS base
    EXPORT laguna-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

#Export the targets to a script
install(EXPORT laguna-targets
    FILE        lagunaTargets.cmake
    NAMESPACE   laguna::
    DESTINATION ${INSTALL_CONFIGDIR}
)

#Create a ConfigVersion.cmake file
include(CMakePackageConfigHelpers)
write_basic_package_version_file(
    ${CMAKE_CURRENT_BINARY_DIR}/lagunaConfigVersion.cmake
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY AnyNewerVersion
)

configure_package_config_file(${CMAKE_CURRENT_LIST_DIR}/cmake/lagunaConfig.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/lagunaConfig.cmake
    INSTALL_DESTINATION ${INSTALL_CONFIGDIR}
)

#Install the config, configversion and custom find modules
install(FILES
    ${CMAKE_CURRENT_BINARY_DIR}/lagunaConfig.cmake
    ${CMAKE_CURRENT_BINARY_DIR}/lagunaConfigVersion.cmake
    DESTINATION ${INSTALL_CONFIGDIR}
)

##############################################
# Exporting from the build tree
export(EXPORT laguna-targets 
    FILE ${CMAKE_CURRENT_BINARY_DIR}/lagunaTargets.cmake
    NAMESPACE laguna::
)

#Register package in user's package registry
export(PACKAGE laguna)

