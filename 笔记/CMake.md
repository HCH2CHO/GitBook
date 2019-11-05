# CMake

文档：<https://cmake.org/cmake/help/v3.15/manual/cmake.1.html>

https://cmake.org/cmake/help/latest/guide/tutorial/index.html

简书：<https://www.jianshu.com/p/8909efe13308>

https://www.jianshu.com/p/bbf68f9ddffa

```cmake
#CMake最低版本
cmake_minium_required (VERSION 2.6)
#定义项目工程名称，并存在PROJECT_NAME中
project (CMakeTest)
#执行命令
add_executable( ${PROJECT_NAME} main.cpp)
```

 

```cmake
#创建hello库
add_library(Hello hello.app hello.h)  
#使用新库创建应用文件
add_executable(executable main.cpp)  
#创建链接到所需库
target_link_libraries( executable Hello )
```

 

```cmake
cmake_minimum_required(VERSION 2.6)
#管理CMake的策略设置
cmake_policy(SET CMP0012)
PROJECT(Chapter2)

#搜索OpenCV依赖项
FIND_PACKAGE(OpenCV 3.0.0 REQUIRED)

MESSAGE("OpenCV version : ${OpenCV_VERSION}")
#添在环境中加指定库的头文件和目录
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIB_DIR})

#创建SRC变量,向其中添加main.cpp
SET(SRC main.cpp)
#创建可执行文件并链接到OpenCV库
ADD_EXECUTABLE(${PROJECT_NAME} ${SRC})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${OpenCV_LIBS}）
```

 

```cmake
#添加子文件夹的CmakeList
add_subdirectory(utils)

#添加预编译器的可选日志
option(WITH_LOG "Build with output logs and images in tmp" OFF)
if(WITH_LOG)
  add_definitions(-DLOG)
endif(WITH_LOG)

target_link_libraries( ${PROJECT_NAME} ${OpenCV_LIBS} Utils)
```

在utils子文件中写

```cmake
#CMAKE_CURRENT_SOURCE_DIR指的是当前处理的CMakeLists.txt所在的路径
target_include_directories(Utils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
```

