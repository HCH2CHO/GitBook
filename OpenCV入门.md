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

