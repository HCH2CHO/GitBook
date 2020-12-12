### QPainter和QGraphicsView

``` 
在Qt界面库中，可以通过以下两种方式进行图形的绘制：
对于普通的二维绘图，可使用QPainter在QWidget、QPixmap等绘图设备上绘图，通过绘制一些基本的点、线、圆等基本形状组成自己需要的图形，这种方式得到的图形是不可交互的图形。

对于需要绘制大量的、需要交互图形，可借助于Graphics View架构，使用QGraphicsView、QGraphicsScenet和各种QGraphicsItem类进行绘制。这种方式可以在一个场景中可绘制大量图元项，且每个图元项都是可选择、可交互的。
```



QtGui.Painter
QtWidgets.QGraphicsItem
QtWidgets.QGraphicsView

QGraphicsItem图形基类
QtWidgets.QGraphicsScene 为QGraphicsItem的容器
QGraphicsView使QGraphicsScene可视化

三者的区别比较
GraphicsView框架结构主要包含三个主要的类QGraphicsScene（场景）、QGraphicsView（视图）、QGraphicsItem（图元）。QGraphicsScene本身不可见，是一个存储图元的容器，必须通过与之相连的QGraphicsView视图来显示及与外界进行交互，主要提供图元的操作接口、传递事件和管理各个图元状态，提供无变换的绘制功能（如打印）；QGraphicsView提供一个可视的窗口，用于显示场景中的图元，一个场景中可以有多个视图。QGraphicsItem是场景中各个图元的基础类，QT提供了常用图形图元的标准类，如矩形(QGraphicsRectItem)、椭（QGraphicsEllipseItem)、文本(QGraphicsTextItem)。
GraphicsView是一个基于图元的Model/View架构的框架，每一个组件都是一个独立的元素。QPainter采用面向过程的描述方式绘图；GraphicsView采用面向对象的描述方式绘图。GraphicsView绘图时首先创建一个场景，然后创建图元对象（如一个直线对象、一个多边形对象），再使用场景的add()函数，将图元对象添加到场景中，最后通过视图进行显示。对于复杂的图像来说，如果图像包含大量的直线、曲线、多边形等图元对象，管理图元对象比管理QPainter的绘制过程语句要容易，并且图元对象更符合面向对象的思想，图形的可复用性更好。



### 信号槽

QT信号槽
信号，发生的事件	QtCore.Signal(int)
连接connect
槽，函数，响应事件	@QtCore.Slot(int)

PySide2.QtCore.QObject.connect(sender, signal, receiver, method)

connect(sender, signal, receiver, slot);

参数：

 sender：发出信号的对象

 signal：发送对象发出的信号

 receiver：接收信号的对象

 method：接收对象在接收到信号之后所需要调用的函数

例：self.connect(lcdRange, QtCore.SIGNAL("valueChanged(int)"), previousRange.setValue)
这条语句作用是把我们定义的LCDRange的对象进行信号和槽连接。
这时connect只有三个参数，第一个是发送这个信号的对象，第二个是要发送的信号，第三个是接收信号的槽。



### 相对路径

./  表示当前路径，相对于**工作目录**的路径。通常指Qt自动生成的目录，而不是其中的debug目录。

:/  表示资源文件路径，对资源的引用，见.qrc文件。



### UI

.exec()是一个循环时间函数



### **踩过的坑**

需要MinGW、MSVC2019混合编译

Debug没过，Release版本通过

需要关闭“项目”里的shadow build

##### 一个bug

![image-20201015142723327](C:\Users\jiaqy11\AppData\Roaming\Typora\typora-user-images\image-20201015142723327.png)

当有这行注释时我的gpstime存不进去数据？？？TMD

经查证，这是由于**CRLF和LF换行符**导致的问题！！！真是活久见。

MSVC编译器应使用CRLF格式

### 打包

打开Qt 5.15 MSVC2019 64-bit

cd  /d  <构建目录/release>

windeployqt  <程序名>



### 格式转换

QString转换String

```
string s = qstr.toStdString();
```

String转换QString

```
QString qstr2 = QString::fromStdString(s);
```




### 快捷键

添加注释：/**

snippets：Tool->Option中的Text Editor->Completion 里的 "Activate completion"，然后可在目标位置触发

F1     查看帮助

F2     跳转到函数定义（和Ctrl+鼠标左键一样的效果）

Shift+F2  声明和定义之间切换

F4     头文件和源文件之间切换

Ctrl+Space  自动补全（貌似会和输入法的切换冲突）我修改为Ctrl+Shit+Space

Alt(按住)+ Enter  将在cpp中添加该函数的定义。

Ctrl+Tab   上一个文件

Ctrl+I     自动对齐

Ctrl+L    跳转到某行

Ctrl+/     注释行，取消注释行

Ctrl+F

Ctrl+Shift+F

Ctrl+,   Ctrl+.   切换书签

F5        开始调试
Shift+F5  停止调试
F10      单步前进
F11      单步进入函数
Shift + F11 单步跳出函数

Ctrl + Shift + R 修改变量名,并应用到所有使用该变量的地方

### Pro头文件

```
#定义变量
PCL_DIR = "D:/PCL 1.11.0"
$${PCL_DIR}

#cJson类库
INCLUDEPATH += $$PWD/thirdparty/json
DEPENDPATH += $$PWD/thirdparty/json
然后在工程中加入对应的h,cpp文件,有点鸡肋的一个步骤
```
