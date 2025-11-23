cmake_minimum_required(VERSION 4.2)

set(CMAKE_CXX_STANDARD 20)

set(NEBULA_RHI_ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR})

project(NebulaRHI)

set(NEBULA_RHI_BACKENDS_SOURCES
    "Source/Backends/Vulkan/VulkanImpl.cpp"
    "Include/Backends/Vulkan/VulkanImpl.hpp"
)

set(NEBULA_RHI_SOURCES 
    "Include/IRenderInterface.hpp"
    "Source/ResourcePool.cpp"
    "Include/ResourcePool.hpp"
    ${NEBULA_RHI_BACKENDS_SOURCES}    
)

add_library(NebulaRHI ${NEBULA_RHI_SOURCES})
target_include_directories(NebulaRHI PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/Include/
)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${NEBULA_RHI_SOURCES})

add_subdirectory(Testing)