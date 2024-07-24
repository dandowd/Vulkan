cmake_minimum_required(VERSION 3.30)
project(MyVulkanProject)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    message(STATUS "AddressSanitizer enabled for Debug build")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fsanitize=address -fno-omit-frame-pointer")
endif()

set(CMAKE_CXX_STANDARD 17)

find_package(Vulkan REQUIRED)
find_package(glfw3 REQUIRED)
find_package(glm REQUIRED)

include_directories(${Vulkan_INCLUDE_DIRS})
include_directories(${GLFW_INCLUDE_DIRS})
include_directories(${GLM_INCLUDE_DIRS})

add_executable(MyVulkanProject src/main.cpp)

target_link_libraries(MyVulkanProject ${Vulkan_LIBRARIES} glfw glm::glm)
