cmake_minimum_required(VERSION 3.10)

project(VulkanGameEngine)

set(CMAKE_TOOLCHAIN_FILE "/home/john/Applications/vcpkg/scripts/buildsystems/vcpkg.cmake")

find_package(Vulkan REQUIRED)

# ADD GLFW3
list(APPEND CMAKE_PREFIX_PATH "/home/john/Applications/vcpkg/installed/x64-linux/share/glfw3/")
find_package(glfw3 CONFIG REQUIRED)

# ADD GLM
list(APPEND CMAKE_PREFIX_PATH "/home/john/Applications/vcpkg/installed/x64-linux/share/glm/")
find_package(glm CONFIG REQUIRED)

include_directories(include)


set(SOURCES ${CMAKE_SOURCE_DIR}/src)
set(INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include)

# All .cpp files in the src directory
file(GLOB SRC_FILES ${SOURCES}/*.cpp)

# All .hpp files in the include directory
file(GLOB HEADER_FILES ${INCLUDE_DIR}/*.hpp)

add_executable(VulkanGameEngine ${SRC_FILES} ${HEADER_FILES})

target_include_directories(VulkanGameEngine PRIVATE ${Vulkan_INCLUDE_DIRS})
target_include_directories(VulkanGameEngine PRIVATE ${INCLUDE_DIR})
target_link_libraries(VulkanGameEngine PRIVATE ${Vulkan_LIBRARIES})
target_link_libraries(VulkanGameEngine PRIVATE glfw)
target_link_libraries(VulkanGameEngine PRIVATE glm::glm)