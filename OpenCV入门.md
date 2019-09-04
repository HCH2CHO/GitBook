## 安装

```
重新安装，解压
cmake-gui

mingw32-make -j8
mingw32-make install
https://blog.csdn.net/qq_25109263/article/details/76945395
```

相对路径  ../hello.jpg表示当前项目目录下，hello.jpg表示编译文件下

## OpenCV基础

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

## OpenCV

#### 安装

```
重新安装，解压
cmake-gui

mingw32-make -j8
mingw32-make install
https://blog.csdn.net/qq_25109263/article/details/76945395
```

viz模块+ vtk库

相对路径  ../hello.jpg表示当前项目目录下，hello.jpg表示编译文件下

PCL点云库

#### OpenCV概述

imgcodes模块：处理图像文件读写、内置数据结构

imgproc模块：图像滤波、形态学操作、几何变换、结构分析、色彩变换、绘制图像、直方图、特征检测

ximgproc模块：高级图像处理算法

highgui模块：用户交互操作、界面

video、videotab模块：视频分析

calib3d模块：三维重建

feature2d、xfeature2d模块：特征提取、检测

bioinspired模块：仿生

objdetect、xobjdetect模块：目标检测

ml、flann模块：机器学习

photo、xphoto、stitching模块：计算摄影shape模块：形状分析

optflow、tracking模块：光流算法、特征跟踪

face、saliency模块：人脸识别、目标识别

text、tesseract_OCR模块：文本检测与识别 

#### 内容1

Mat类 	图像、矩阵

imread()

imwrite()

clone()

CV_number_typeC(n)		n是通道数

convertTo()

Vec3b类

CommandLineParser 命令行解析器

parser.printMessage()

printErrors()

parser.has()

parser.get<string>(0)  访问读取输入参数

parser.check()

VideoCapture相机类

release()

nameWindow创建窗口

destroyAllWindows()

“>>”获取帧

waitKey() 等待任意键（毫秒）

Vec类	向量

Scalar类		Vec派生类，4个元素

Point类

Size类		尺寸(宽高)、面积函数area()

Rect类		2D矩形，ROI

RotatedRect类	旋转矩形

#### 内容2

矩阵：t() 转置， inv() 求逆

#### 内容3

XML/YAML持久化层

FileStorage类	创建写入、读取

namedWindow()	创建窗口

moveWindow()	移动窗口

resizeWindow()	调整大小

destoryWindow()	

createTrackbar()	创建滑动条

setMouseCallback()	创建鼠标事件

circle()	绘制圆形

createButton()

blur()	模糊滤波

Sobel()	索贝尔滤波

cvtColor()	色彩空间转换

#### 内容4

split()	 将图像分割成三通道

calcHist()	计算直方图

normalize()	归一化

equalizeHist()	均衡化

merge()		合并结果通道

LUT()		查找表

medianBlur()		中值滤波

Canny()		边缘检测

getStructuringElement()	边缘膨胀

bilateralFilter()	双边滤波器

AOI

图像差分

threshold()	二值化

connectedComponents()	连通区域算法

findContours()	目标分割

drawContours()	绘制

StatModel

