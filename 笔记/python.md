```python
if __name__ == '__main__':
```

- **如果全局变量是int或者str，那么如果要在函数中对其进行修改，则需先在函数内声明其为global。如果是list或者dict可直接修改**。
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

  eval（）

- ileObject.seek(offset[, whence])

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

line = line.strip()  去掉头尾空白

os.popen(‘ ’）调用命令行

- 数据结构 list，dict，tuple，set
- from collections import Counter   计数
- \  代码太长换行，;  交互端换行

```
/usr/bin/pip3
1. from pip import __main__
2. if name == '__main__':
3. sys.exit(__main__._main())
```



    Python中符合序列的有序序列都支持切片（slice），例如列表，字符串，元组。
    格式：【start:end:step】
    start:起始索引，从0开始，-1表示结束
    end：结束索引
    step：步长，end-start，步长为正时，从左向右取值。步长为负时，反向取值
```
通过__dict__，就可以动态的获取到对象的全部属性。
```

"="浅拷贝问题：

​	"="对简单变量为赋值操作，对list、dict等复杂对象为复制对象引用，即浅拷贝。

```
struct库：
		struct.pack()
		struct.unpack()
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

### pip

pip换源

pip install spyder -i  http://mirrors.aliyun.com/pypi/simple/



spyder快捷键：<https://blog.csdn.net/weixin_41500849/article/details/80298944>

spyder官网：

<https://docs.spyder-ide.org/>