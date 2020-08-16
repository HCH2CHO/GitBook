## python对象

python中一切变量皆为对象。

python内置的一些类型中

- 可变对象：list dict set  ——相当于引用
- 不可变对象：tuple string int float bool  ——相当于真值

## Tip

```python
if name == 'main':
```

```python
try:
	pass
except Exception as e:
	print(e)
finally:
    pass
```



```python
#python包声明
__init__.py
#__all__控制*所引入的模块/函数/类
__all__=['a.py','b.py']
```



```python
特殊注释
# TODO
```

- os.getcwd()  获取当前路径


- os.walk(path),遍历path，返回一个对象，他的每个部分都是一个三元组,('目录x'，[目录x下的目录list]，目录x下面的文件)。topdown为True遍历子目录。

~~~python
for root, dirs, files in os.walk(dir, topdown=True):  
        for name in files:  
            print os.path.join(root, name)  
        for name in dirs:  
            print os.path.join(root, name)  
~~~

- ../  上一级目录

- reset 清空变量

  reset out 清空输出

  reset in 清空输入

- 正则表达式

  `re.sub('[\r\n\t]', '', s)`  去除\r\n\t字符

- 字典d

  d['Paul'] = 72 

- 字符串转列表、字典    

  eval()    repr()/str()

- fileObject.seek(offset[, whence])

  * **offset** -- 开始的偏移量，也就是代表需要移动偏移的字节数
  * **whence：**可选，默认值为 0。给offset参数一个定义，表示要从哪个位置开始偏移；0代表从文件开头开始算起，1代表从当前位置开始算起，2代表从文件末尾算起

- re.search

  span（）

  line[a:b]

- Python会在以下路径中搜索模块：

  ​	程序所在文件夹

  ​	标准库的安装路径

  ​	系统环境变量PYTHONPATH所包含的路径

- 多维列表初始化

  multilist = [[0 for col in range(5)] for row in range(6)]

- enumerate()

  用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。


%matplotlib inline  在终端显示

%matplotlib qt5    在窗口显示

```
numpy:a=np.array([1,2,3])  
```

- line = line.strip()  去掉头尾空白

- os.popen(‘ ’）调用命令行

- 数据结构 list，dict，tuple，set
- from collections import Counter   计数
- \  代码太长换行，;  交互端换行

    Python中符合序列的有序序列都支持切片（slice），例如列表，字符串，元组。
    格式：【start: end: step】
    start:起始索引，从0开始，-1表示结束
    end：结束索引
    step：步长，end-start，步长为正时，从左向右取值。步长为负时，反向取值
```
通过__dict__，就可以动态的获取到对象的全部属性。
```

- "="浅拷贝：
  	"="对简单变量为赋值操作，对list、dict等复杂对象为复制对象引用，即浅拷贝。

- cpoy类的深拷贝与浅拷贝：
  	copy.copy()：不复杂对象如数值、字符串、元组可直接复制，复杂对象仍为指针形式
    	copy.deepcopy()：被复制对象完全再复制一遍作为独立的新个体单独存在

```
struct库：
		struct.pack()
		struct.unpack()
```



```python
@property		#把方法『变成』了属性。鸡肋的设计，可在赋值时加入范围检查、加密处理等函数

使用@staticmethod或@classmethod，就可以不需要实例化，直接类名.方法名()来调用
@staticmethod	#当方法中不需要访问任何实例方法和属性，纯粹地通过传入参数并返回数据的功能性方法
@classmethod	#用它来修饰的方法，其第一个参数不是self，而是cls，也就是这个类本身作为参数。相比于staticmethod，classmethod可以判断出自己是通过基类被调用，还是通过某个子类被调用
```

- 单星号参数*和双星号参数**

  函数中的单星号参数代表此处接受任意多个**非关键字**参数，这些参数将以tuple元组形式保存

  函数中的多星号参数代表此处接受任意多个**关键字**参数，这些参数以字典形式保存

### 全局变量问题

- **PEP8不鼓励在函数中修改全局变量**
- 在函数中，当不需要对全局变量赋值时直接使用；当需要赋值时要先在函数中声明global，否则视为赋值定义局部变量。建议全局变量命名前加g_

> 如果全局变量是int或者str，那么如果要在函数中对其进行修改，则需先在函数内声明其为global。如果是list、dict等复杂对象可直接修改（不建议）。

> 函数中可使用全局变量，但不能对其赋值。如果赋值则该变量在函数中其表示为局部变量（函数不能修改全局变量）。当想要修改该全局变量时，可使用global在函数内进行声明（然而PEP8标准不建议修改）

### socket网络

https://www.cnblogs.com/aylin/p/5572104.html

```python
#线程守护，当主线程结束时，子线程会一并结束
thread.setDaemon(True)

#I/O多路复用指
select.select()  #轮询
ThreadingTCPServer
selectors
SocketServer

#端口复用。端口复用前需要先close()，否则会收不到数据
sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

#阻塞式多线程占用资源
#select 效率较低


```

## Python 配置

 py --list-paths 查看所有python版本

```
/usr/bin/pip3
1. from pip import __main__
2. if name == '__main__':
3. sys.exit(__main__._main())
```



## Jupyter Notebook

* **Shift-Enter** : 运行本单元，选中下个单元
* **Ctrl-Enter** : 运行本单元
* **D,D** : 删除选中的单元

修改jupyter保存文件目录：https://blog.csdn.net/lyxuefeng/article/details/79469189

## Pandas

```python
读取文件按uid列计数，并导出
import pandas as pd
df=pd.read_csv('UserMovie_train.txt',delimiter='\t')
gp=df.groupby('uid').size().reset_index()
gp.to_csv('test1.csv')
```

## pip

pip换源

临时：pip install spyder -i  https://mirrors.aliyun.com/pypi/simple/

永久：pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/

pip -V  查看pip信息

spyder快捷键：<https://blog.csdn.net/weixin_41500849/article/details/80298944>

spyder官网：

<https://docs.spyder-ide.org/>



## python加速

Pypy

Cython

numba

```
#优化for循环及numpy，使用循环中全局变量易出问题
from numba import jit
@jit
def fun()
```

C++  调用python

python 调用C++



## 面向对象

继承往往和多态一起使用，继承的本质是为了实现多态，不是简单的代码复用。但继承会造成代码可读性更为复杂。

继承的功能可以用组合的方式实现，鸡肋的继承。



## 关于python的吐槽

python用于工程项目当中确实蛮麻烦。

- 没有逻辑体{  }的设计，仅依靠对齐来表示层级。容易在调试中因为误触一个键导致某一行某几行位置出错，从而逻辑不对
- 动态类型。我想大多数人其实并不想用动态类型。代码写多了才明白大道至简的道理。动态类型一方面影响了python的速度，另一方面还容易导致开发中出错
- 但是我真的喜欢python简洁的语法

