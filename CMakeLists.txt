cmake_minimum_required(VERSION 3.5)
project(ai_utils_msgs)

find_package(catkin QUIET)
find_package(ament_cmake QUIET)

if(${catkin_FOUND})

    find_package(std_msgs REQUIRED)
    find_package(geometry_msgs REQUIRED)
    find_package(message_generation REQUIRED)
    find_package(message_runtime REQUIRED)

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


elseif(${ament_cmake_FOUND})

    find_package(rosidl_default_generators REQUIRED)
    find_package(std_msgs REQUIRED)
    find_package(geometry_msgs REQUIRED)

    rosidl_generate_interfaces(${PROJECT_NAME}
    "msg/Object.msg"
    "msg/ObjectArray.msg"
    "srv/ComputeInference.srv"
    DEPENDENCIES std_msgs geometry_msgs
    LIBRARY_NAME ${PROJECT_NAME}
    )

    ament_export_dependencies(rosidl_default_runtime)

    ament_package()

endif()