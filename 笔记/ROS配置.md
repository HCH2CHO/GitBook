## **iau_ros_map**

运行Clion

```
./Documents/clion/bin/clion.sh
```



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



查看ros版本

```
roscore
rosparam list
rosparam get /rosdistro
```

