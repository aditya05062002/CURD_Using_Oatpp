cmake_minimum_required(VERSION 3.14)

project(my_crud_app)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add the vcpkg toolchain file
set(CMAKE_TOOLCHAIN_FILE "${CMAKE_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")

# Add executable
add_executable(my_crud_app 
    src/App.cpp
    src/DTOs.hpp
    src/Database.hpp
    src/Database.cpp
    src/Controller.hpp
)

# Find oatpp and oatpp-swagger packages
find_package(oatpp CONFIG REQUIRED)
find_package(oatpp-swagger CONFIG REQUIRED)

# Link oatpp libraries
target_link_libraries(my_crud_app PRIVATE 
    oatpp::oatpp
    oatpp::oatpp-swagger
)
