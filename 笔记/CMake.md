# CMake

文档：<https://cmake.org/cmake/help/v3.15/manual/cmake.1.html>

https://cmake.org/cmake/help/latest/guide/tutorial/index.html

[CMake 入门实战 | HaHack](https://www.hahack.com/codes/cmake/)

博客：<https://www.jianshu.com/p/8909efe13308>

https://www.jianshu.com/p/bbf68f9ddffa	源码在Cmake源文件的Help/guide/tutorial中。

```bash
#默认编译器编译
mkdir build
cd build
cmake ..
cmake --build .
```

```bash
#选择mingw编译
cmake .. -G "MinGW Makefiles"
mingw32-make
```



## 说明

- CMake 不区分大小写
- project命令会隐式地定义<projectname> _BINARY_DIR 和<projectname> _SOURCE_DIR 两个变量。PROJECT_BINARY_DIR同<projectname> _BINARY_DIR。
- ${} 表示变量
- set()和list(append )作用相同，设置变量
- target_include_directories(<target>  <INTERFACE|PUBLIC|PRIVATE>  [item])  包括头文件查找目录

## 来自教程

1.基础

```cmake
cmake_minimum_required(VERSION 3.10)
# set the project name
project(Tutorial)
# add the executable
add_executable(Tutorial0 tutorial.cxx)
```

2.添加头文件

```cmake
cmake_minimum_required (VERSION 2.6)
project (Tutorial)
# The version number.
set (Tutorial_VERSION_MAJOR 1)
set (Tutorial_VERSION_MINOR 0)
 
# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )
 
# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")
 
# add the executable
add_executable(Tutorial tutorial.cxx) 
```

3.添加库

```cmake
#子文件夹
add_library(MathFunctions mysqrt.cxx)
```

```cmake
# add the MathFunctions library?
if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
  add_subdirectory (MathFunctions)
  set (EXTRA_LIBS ${EXTRA_LIBS} /MathFunctions)
endif (USE_MYMATH)

# add the executable
add_executable (Tutorial tutorial.cxx)
target_link_libraries (Tutorial  ${EXTRA_LIBS})
```

4.添加安装和测试

```bash
# add the install targets
install (TARGETS Tutorial DESTINATION bin)
install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"      DESTINATION include)

enable_testing()
# does the application run
add_test (TutorialRuns Tutorial 25)

# does it sqrt of 25
add_test (TutorialComp25 Tutorial 25)
set_tests_properties (TutorialComp25   PROPERTIES PASS_REGULAR_EXPRESSION "25 is 5")
```



## 来自OpenCV

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

