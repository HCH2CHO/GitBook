```
重新安装，解压
cmake-gui

mingw32-make -j8
mingw32-make install
https://blog.csdn.net/qq_25109263/article/details/76945395
```

相对路径  ../hello.jpg表示当前项目目录下，hello.jpg表示编译文件下

# CMake

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
#添在环境中加制定库的头文件和目录
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIB_DIR})


#创建SRC变量,向其中添加main.cpp
SET(SRC main.cpp)
#创建可执行文件并链接到OpenCV库
ADD_EXECUTABLE(${PROJECT_NAME} ${SRC})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${OpenCV_LIBS
```

 

```cmake
#添加子文件夹的CmakeList
add_subdirectory(utils)


#添加预编译器的可选日志
option(WITH_LOG "Build with output logs and images in tmp" OFF)
if(WITH_LOG)
  add_definitions(-DLOG)
endif(WITH_LOG)


target_link_libraries( ${PROJECT_NAME} ${OpenCV_LIBS} Utils
```

在utils子文件中写

```cmake
#CMAKE_CURRENT_SOURCE_DIR指的是当前处理的CMakeLists.txt所在的路径
target_include_directories(Utils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
```

# OpenCV

- Mat类存储图像、矩阵

```
Mat(nrows,ncols,type,fillValue)
DataType类: CV_<bit depth>{U|S|F}C(<number of channels>)
```

 

所有的 OpenCV 类和函数都在 cv 命名空间（namespace）中，因此，在源代码中还有如下两个选项：

1. 在包含头文件后还应添加使用命名空间 cv 的声明（u[sin](http://c.biancheng.net/ref/sin.html)g namespace cv）（这是本书所有代码示例所使用的选项）。
2. 对用到的所有 OpenCV 类、函数和数据结构上附加 cv:: 前缀。如果由 OpenCV 提供的外部名字与常用的标准模块库（s[tan](http://c.biancheng.net/ref/tan.html)dard template library，[STL](http://c.biancheng.net/stl/)）或其他库冲突，那么就推荐使用这个选项。

```
读取图片
Mat imread(const String& filename,int flags = IMREAD_COLOR)
写入图片
bool imwrite(const String& filename,InputArray img,const vector<int>& params=vector<int>())
检查
.empty() 
创建窗口
void namedWindow(const String& winname,int flags = WINDOW_AUTOSIZE)
显示图像
void imshow(const String& winname,InputArray mat)
改变图像的颜色空间
cvtColor()
```

.hpp文件记录参数的枚举

在一个程序结束时，会隐式地完成资源的释放。

```
int waitKey(int delay=0)
这个函数在数毫秒（delay>0）内等待一个按键操作，并返回键的编码，如果延迟结束时没有按键则返回 -1。如果 delay 是 0 或负数，那么函数一直等待直到一个键被按下。
```

 

VideoCapture 类和 VideoWriter 类为视频处理中所涉及的捕获和记录任务提供了一个易用的C++ API。

```
 VideoCapture inVid(O) ; //打开默认摄像机
 inVid.release(); // 关闭摄像机
```

 

at()函数读取矩阵重某个像素

迭代器MatIterator

.row()  .col() 获取行列