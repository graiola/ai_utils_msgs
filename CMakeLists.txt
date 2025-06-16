cmake_minimum_required(VERSION 3.5)
project(ai_utils_msgs)

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
