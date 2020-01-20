## Linux工具

[https://github.com/linw7/Skill-Tree/blob/master/Linux%E5%B7%A5%E5%85%B7.md](https://github.com/linw7/Skill-Tree/blob/master/Linux工具.md)

man +命令  查询命令使用

```bash
xinput	#查看输入
xinput --disable 11	#关闭触摸板
xinput --enable 11	#开启触摸板
```

## bash

`sudo -s` 切换root用户

切换用户  `su  username`

同时切换用户环境`su  -  username`

`rm -rf`  删除文件

`cd ..` 返回上一层

`cp` 复制

`lsb_release -a`  查看linux版本

`mv`  移动文件到

`killall python` 切掉全部python进程

`tar -zxvf` 解压.tar.gz文件

```
cat  filename  一次显示整个文件
cat  >  filename
cat   file1   file2  > file	将几个文件合并为一个文件
```

```
scp -P 5678 jqy@47.254.24.30:/home/jqy/a.csv v.csv
scp root@192.168.1.155:1.txt 2.txt （把服务器的1.txt下载到本地，并且重命名为2.txt）
scp 2.txt root@192.168.1.155:3.txt （把本地2.txt文件上传到服务器的root目录下，并且命名为3.txt）
```

`pip install mat -i https://pypi.douban.com/simple`   #利用国内镜像安装

````
jupyter notebook --ip=0.0.0.0 --port 8000 --no-browser --allow-root     
--ip指定ip --no-browser不打开浏览器 --allow-root允许root运行 --port 8000 在端口8000下运行
jupyter notebook --allow-root &
jupyter notebook --allow-root --port 8000 &
````

`nohup python3 -u xDeepFM.py > nohup.out 2>&1 &`   在后台运行python程序

`nohup python3 -u model_5.py > nohup5.out 2>&1 &`

`ls -al`  查看软连接

```
netstat -tunlp 查看端口占用情况
```

```
telnet  [ip] 22  查看某端口连接情况
```

lsof -i:8000  查看某端口

kill -9 8000  关闭8000进程

`chmod 777 file`  修改文件权限

nmap 127.0.0.1    查看本地开放端口

`vim ~/.jupyter/jupyter_notebook_config.py`

workon+两次Tab键会提示所有虚拟环境

`nvidia-smi` 查看显卡信息

`df -hl`  检查磁盘空间

`du -lh --max-depth=1` 显示文件夹大小

`ls -lht` 显示当前文件夹下各文件大小

du -sh

`free -m`查看服务器内存

`%matplotlib qt`  spyder在窗口显示图片

pip list 查看安装的库。在pip 安装库后==1.9.0  指定安装版本

`cat /etc/issue`  系统安装时默认的发行版本信息

`pip -V  `查看版本

`nvidia-smi`  查看GPU情况

`scp /data/xDeepFM/ex_data/dataset1.txt ubuntu@106.75.225.80:/data/xDeepFM/ex_data/ ` 服务器互传文件

Ctrl+a  Ctrl+e   行头行尾

`head   file` 查看文件前几行

```
Anaconda下启动虚拟环境
export PATH=/home/ubuntu/anaconda3/bin:$PATH
source activate deeptrain
source deactivate        
```

whereis nginx.conf  语句

history  查看历史操作

/etc/init.d/apache2 start

`ls -l | grep python ` 查看软连接

`wegt -c  +链接 ` 下载文件.  -b后台下载，-c断点续传

pwd	显示当前目录

sudo nautilus	以管理员权限打开文件夹

shutdown -c now 立即重启

iptables	控制端口



## 快捷键

```
Tab  自动补全
Ctrl+a 光标移动到开始位置
Ctrl+e 光标移动到最末尾
Ctrl+k 删除此处至末尾的所有内容
Ctrl+u 删除此处至开始的所有内容
Shift+Ctrl+C 复制
Shift+Ctrl+V 粘贴
CTRL + ALT + T 打开终端
```



## 权限问题

![img](http://tinywan-develop.oss-cn-hangzhou.aliyuncs.com/18-11-13/58024930.jpg)

```
drwxr-xr-- 表示用户权限为：读、写、执行；用户组权限：读、执行；其他权限：读，不能写和执行
-rw-rw-r-- 表示用户权限为：读、写；用户组权限：读、写；其他权限：读，不能写和执行
0123456789（这里，我写个标号，为了后面说明问题方便使用）

这里显示的权限是依次排列的，分别为：[用户][同组][其他]
用户权限，就是你自己的权限。英文：user，简写：u（覆盖标号123）
用户组权限，就是和你同组的人的权限。英文：group，简写：g（覆盖标号456）
其他权限，就是不和你同组的人的权限。英文：others，简写：o（覆盖标号789）
所有人的权限，英文：all，简写：a

r, 即Read，读，权限值为4
w，即Write，写，权限值为2
x，即eXecute，执行，权限值为1
-，在标号0位置，表示普通的文件
-，其他位置，表示对应权限未开启，不具备权限
d，即directory，表示目录文件

无任何权限：数字0表示
开所有权限：数字7表示，即7=4+2+1

chmod 命令是用于改变文件或目录的访问权限。

+ 表示增加权限，如u+x, u+r, u+w, g+w, g+r, o+r， a+r等
- 表示取消权限，如u-x, u-r, u-w, g-w, g-r, o-r， a-r等
= 表示赋予给定权限，并取消其他所有权限（如果有的话，如原来u是rwx，设置u=r，u就剩r）
```

