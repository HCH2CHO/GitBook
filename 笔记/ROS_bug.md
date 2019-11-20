### 错误一：

```
CMake Error: The source "/home/kinrua/catkin_ws/src/CMakeLists.txt" does not match the source "/home/kinrua/catkin_ws/src/iau_ros_map/CMakeLists.txt" used to generate cache.  Re-run cmake with a different source directory.
Invoking "cmake" failed
```

原因：使用了其他cmake进行编译。

解决：删除build下文件，使用catkin_make重新编译



### 错误二：

```
By not providing "Findcatkin.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "catkin", but
  CMake did not find one
 
 Could not find a package configuration file provided by "catkin" with any
  of the following names:

    catkinConfig.cmake
    catkin-config.cmake

  Add the installation prefix of "catkin" to CMAKE_PREFIX_PATH or set
  "catkin_DIR" to a directory containing one of the above files.  If "catkin"
  provides a separate development package or SDK, be sure it has been
  installed.
```

原因：clion默认的CMake为Bundled，且CMake上没进行设置。参见https://blog.csdn.net/u013110229/article/details/87697252 。

**Clion打开方式问题！！！**使用./clion.sh打开编译无问题。

快捷方式Exec=bash -i -c "/home/kinrua/Documents/clion/bin/clion.sh" %f

解决：修改Settings->Build->CMake中的设置，修改Settings->Build->Toolchains中CMake设置。该方案连续点击容易导致程序卡死，可修改环境变量export PATH=$PATH:～/Documents/clion/bin从而从终端直接启动clion.sh



### 错误三：

重启电脑后roscore无法运行。

原因：~/.bashrc中有source /home/kinrua/catkin_ws/devel/setup.bash，影响source /opt/ros/melodic/setup.bash

解决：source /opt/ros/melodic/setup.bash