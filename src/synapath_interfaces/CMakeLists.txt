cmake_minimum_required(VERSION 3.8)
project(synapath_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)  # 自定义消息依赖

# ------------ 自定义 msg 文件 ------------
find_package(rosidl_default_generators REQUIRED)
set(interface_files    # 在此添加 .msg 文件
  "msg/UWBMsg.msg"   # UWB msg
)
rosidl_generate_interfaces(${PROJECT_NAME}
  ${interface_files}
  DEPENDENCIES builtin_interfaces std_msgs
)


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
