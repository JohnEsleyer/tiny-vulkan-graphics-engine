cmake_minimum_required(VERSION 3.10)

project(VulkanGameEngine)

find_package(Vulkan REQUIRED)

set(SOURCES
    src/main.cpp
)

add_executable(VulkanGameEngine ${SOURCES})

target_include_directories(VulkanGameEngine PRIVATE ${Vulkan_INCLUDE_DIRS})
target_link_libraries(VulkanGameEngine PRIVATE ${Vulkan_LIBRARIES})
