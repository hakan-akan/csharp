cmake_minimum_required (VERSION 3.13)

project (sharp-app-prj)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set (app_name sharp-app)

find_package(laguna 1.0 REQUIRED)

set(CMAKE_CXX_STANDARD 17)  
set(CMAKE_CXX_STANDARD_REQUIRED ON) 
set(CMAKE_CXX_EXTENSIONS OFF)  

add_executable(${app_name}
    src/main.cpp
)

target_include_directories(${app_name}
PRIVATE
)

target_link_libraries(${app_name}
PRIVATE

)

install(TARGETS ${app_name}
        RUNTIME DESTINATION bin
)
