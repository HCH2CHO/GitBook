给Qt配置VTK

将QVTKWidgetPlugin.dll放到Qt5.14.1\Tools\QtCreator\bin\plugins\designer目录下



### 坑

vtk代码编译后不会被拷贝到release、debug目录下，需要手动复制过去



pcl库的std::max()错误

改正方法一：改为(std::max)

方法二：在**导致该错误的文件**头前面加#define NOMINMAX

