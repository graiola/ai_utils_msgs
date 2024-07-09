cmake_minimum_required(VERSION 3.5)
project(ai_utils_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(catkin REQUIRED roscpp std_msgs geometry_msgs message_generation message_runtime genmsg)

add_message_files(FILES
    Object.msg
    ObjectArray.msg
)

add_service_files(
    FILES
    ComputeInference.srv
)

generate_messages(
    DEPENDENCIES
    std_msgs
)

catkin_package()
