## Clion

运行Clion

```
./Documents/clion/bin/clion.sh
```



添加桌面快捷方式

```
cd usr/share/applications/ 
touch clion.desktop
vim clion.desktop
```



修改clion快捷方式设置，注意修改Exec和Icon路径

```
[Desktop Entry]
Encoding=UTF-8

Name=CLion

Comment=clion-2018.1.1

Exec=/home/sqwlly/Downloads/clion-2018.1.1/bin/clion.sh

Icon=/home/sqwlly/Downloads/clion-2018.1.1/bin/clion.svg

Categories=Application;Development;Java;IDE

Version=2018.1.1

Type=Application

#Terminal=1
```

## iau_ros_map

编译iau_ros_map文件

```
编译rosrun iau_ros_map iau_ros_map_ui_node  运行文件
catkin_make iau_ros_msgs_gencpp  单独编译catkin_make iau_ros_msgs文件
roscore		启动ros程序
```



iau_ros_map配置信息

```
CMake Debug
	debug options:-DCATKIN_DEVEL_PREFIX:PATH=/home/kinrua/catkin_ws/devel
	generation path:/home/kinrua/catkin_ws/build
```



## ROS命令行

查看ros版本

```
roscore
rosparam list
rosparam get /rosdistro
```



查看ROS环境变量

```
export | grep ROS
```



## vscode下配置ROS

https://blog.csdn.net/weixin_35695879/article/details/85254422

修改c_cpp_properties.json中的includePath

```shell
catkin_make -DCMAKE_EXPORT_COMPILE_COMMANDS=Yes
#这个命令会输出一个compile_commands.json文件在ROS工作空间的build文件夹下面
#然后在c_cpp_properties.json文件添加下面一段话
"compileCommands": "${workspaceFolder}/build/compile_commands.json"
#workspaceFolder根据实际修改
```

