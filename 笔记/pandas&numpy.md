numpy以行为单位索引，pandas以列为单位索引

# Numpy

#### 获得数组信息

```python
import numpy as np

# 获得数组的维数个数
np_array.ndim

# 获得数组的形状
np_array.shape

# 获得数组中总的元素个数
np_array.size

# 数组元素的类型
np_array.dtype
```

#### 创建数组

```python
import numpy as np
### 通过直接给出的数据创建数组，可以使用 list 或 tuple
### 可以直接指定数组元素的类型
np_array = np.array([[ 0,  1,  2,  3,  4],
                     [ 5,  6,  7,  8,  9],
                     [10, 11, 12, 13, 14]])
np_array = np.array([(1.5,2,3), (4,5,6)], dtype=float)

### 有时数组的内容可能是未知的，但想要初始化一个以后再使用。有许多函数实现。

# 创建一个 3*4 的数组，内容初始化为 0
np.zeros((3,4))

# 创建一个 2*3*4 的数组，内容为 1
np.ones((2,3,4), dtype=np.int16) 

# 创建一个 2*3 的空数组
np.empty((2,3))

### 也可以使用某些模式创建数组

# 创建一个内容从 10 到 30 的一维数组，间隔为 5
np.arange( 10, 30, 5 )

# 创建一个内容从 0 到 2 的一维数组，间隔为 0.3
np.arange( 0, 2, 0.3 ) 

# 创建一个从 0 到 2 有 9 个等间隔的元素组成的一维数组
np.linspace( 0, 2, 9 )
```

#### 基本算法

```python
# 在 Numpy 中，数组上的算术运算符总是应用在元素上。 填充一个新数组并返回结果。

# 例如，如果创建 a 和 b 2个数组，并从 a 中减去 b，将得到下面的结果
# 不能用不同大小的数组执行类似的操作，否则会出现错误
a = np.array( [20,30,40,50] )
b = np.array( [0, 1, 2, 3] )
c = a - b
c = [20, 29, 38, 47]

# 还可以在整个数组上执行元素的标量操作
b**2
b = [0, 1, 4, 9]

# 甚至应用函数
10*np.sin(a)
a = [ 9.12945251, -9.88031624,  7.4511316 , -2.62374854]

# 请记住两个数组间的操作总是应用在每个元素上的
a = np.array( [20,30,40,50] )
b = np.array( [0, 1, 2, 3] )
c = a * b
c = [0, 30, 80, 150]

# numpy 中有许多快速有用的函数，可以经常使用这些函数
a = np.array( [20,30,40,50] )
a.max() # 50
a.min() # 20
a.sum() # 140

# 如果是多维的数组，可以使用 axis 参数
b = np.arange(12).reshape(3,4)
b = [[ 0,  1,  2,  3],
     [ 4,  5,  6,  7],
     [ 8,  9, 10, 11]]

b.sum(axis=0) # [12, 15, 18, 21]
b.min(axis=1) # [0, 4, 8]
b.cumsum(axis=1) # [[ 0,  1,  3,  6], [ 4,  9, 15, 22], [ 8, 17, 27, 38]]

# 如果有需要，还有更多的数学函数
b = np.arange(3)
b = [0, 1, 2]

np.exp(b) # [ 1.0, 2.71828183, 7.3890561 ]
np.sqrt(b) # [ 0.0 ,  1.0, 1.41421356]
np.floor(np.exp(b)) # [ 1.0, 2.0, 7.0 ]
np.round(np.exp(b)) # [ 1.0, 3.0, 7.0 ]

np.c_[a,b]#列合并
np.r_[a,b]#行合并
np.insert(a, 0, values=b, axis=1)#axis=0插入行，axis=1插入列
```

#### 数组切片和变形

```python
# Numpy 数组可以像Python列表一样被索引，切片和迭代
a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
a[2] # 2
a[2:5] # [2, 3, 4]
a[-1] # 10
a[:8] # [0, 1, 2, 3, 4, 5, 6, 7]
a[2:] # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 可以在多维数组上做同样的操作！ 只需使用逗号分隔即可
b = [[ 0,  1,  2,  3],
     [10, 11, 12, 13],
     [20, 21, 22, 23],
     [30, 31, 32, 33],
     [40, 41, 42, 43]]

b[2,3] # 23
b[0:5, 1]  # b 的第二列元素 --> [ 1, 11, 21, 31, 41]
b[ : ,1]   # 和上面相同 --> [ 1, 11, 21, 31, 41]
b[1:3, : ] # b 数组中第二行和第三行的元素 --> [[10, 11, 12, 13], [20, 21, 22, 23]]

# 从第一轴开始完成对多维数组的迭代
for row in b:
  print(row)
# [0 1 2 3]
# [10 11 12 13]
# [20 21 22 23]
# [30 31 32 33]
# [40 41 42 43]
```

#### 更多的技巧

```python
### 这些都是可以使用的 Numpy 数据类型

np.int64 # 有符号 64 位 int 类型
np.float32 # 标准双精度浮点类型
np.complex # 由128位的浮点数组成的复数类型
np.bool # TRUE 和 FALSE 的 bool 类型
np.object # Python 中的 object 类型
np.string # 固定长度的 string 类型
np.unicode # 固定长度的 unicode 类型

### Numpy 数组可以像算数那样直接比较

a = np.array([1, 2, 3])
b = np.array([5, 4, 3])

# 如果直接比较会得到每一个元素的 bool 值
a == b # array([False, False, True])
a >= 2 # array([False, True, True])

# 如果要比较整个数组，可以使用 Numpy 内置的函数
np.array_equal(a, b) # False

# 可以以数轴为单位排序
c = np.array([[2, 4, 8], [1, 13, 7]])
c.sort(axis=0) # array([[1, 4, 7], [2, 13, 8]])
c.sort(axis=1) # array([[2, 4, 8], [1, 7, 13]])

### 使用 Numpy 内置函数可以轻松的完成数组处理

# 转置数组
d = np.transpose(c)

# 更改数组的形状
c.ravel() # 可以使数组变成一维数组
c.reshape((3, 2)) # 将数组的形状从 (2, 3) 改为 (3, 2)

# 增加或删除元素
np.append(c, d) # 将 c 中元素添加到 d 数组中
np.insert(a, 1, 5, axis=0) #  在轴 0 的索引 1 处插入 5
np.delete(a,[1], axis=1) # 删除列，索引 1 处的元素

# 合并数组
np.concatenate((c,d),axis=0)  # 合并数组 c 和 d 轴 0 上的元素
np.vstack((c,d),axis=0)  # 垂直合并数组 c 和 d (行方式)
np.hstack((c,d),axis=0)  # 水平合并数组 c 和 d (列方式)
```



# Pandas

```
pandas-profiling，一行代码生成超详细数据分析报告
```

##### 基本数据集操作

（1）读取 CSV 格式的数据集

```
pd.DataFrame.from_csv("csv_file")
```

或者：

```
pd.read_csv("csv_file")
```

（2）读取 Excel 数据集

```
pd.read_excel("excel_file")
```

（3）将 DataFrame 直接写入 CSV 文件

如下采用逗号作为分隔符，且不带索引：

```
df.to_csv("data.csv", sep=",", index=False)
```

（4）基本的数据集特征信息

```
df.info()
```

（5）基本的数据集统计信息

```
print(df.describe())
```

(6) Print data frame in a table

将 DataFrame 输出到一张表：

```
print(tabulate(print_table, headers=headers))
```

当「print_table」是一个列表，其中列表元素还是新的列表，「headers」为表头字符串组成的列表。

（7）列出所有列的名字

```
df.columns
```

##### 基本数据处理

（8）删除缺失数据

```
df.dropna(axis=0, how='any')
```

返回一个 DataFrame，其中删除了包含任何 NaN 值的给定轴，选择 how=「all」会删除所有元素都是 NaN 的给定轴。

（9）替换缺失数据

```
df.replace(to_replace=None, value=None)
```

使用 value 值代替 DataFrame 中的 to_replace 值，其中 value 和 to_replace 都需要我们赋予不同的值。

（10）检查空值 NaN

```
pd.isnull(object)
```

检查缺失值，即数值数组中的 NaN 和目标数组中的 None/NaN。

（11）删除特征

```
df.drop('feature_variable_name', axis=1)
```

axis 选择 0 表示行，选择表示列。

（12）将目标类型转换为浮点型

```
pd.to_numeric(df["feature_name"], errors='coerce')
```

将目标类型转化为数值从而进一步执行计算，在这个案例中为字符串。

（13）将 DataFrame 转换为 NumPy 数组

```
df.as_matrix()
或
df.values
```

（14）取 DataFrame 的前面「n」行

```
df.head(n)
```

（15）通过特征名取数据

```
df.loc[feature_name]
```

##### DataFrame 操作

（16）对 DataFrame 使用函数

该函数将令 DataFrame 中「height」行的所有值乘上 2：

```
df["height"].apply(*lambda* height: 2 * height)
```

或：

```
def multiply(x):

 return x * 2

df["height"].apply(multiply)
```

（17）重命名行

下面代码会重命名 DataFrame 的第三行为「size」：

```
df.rename(columns = {df.columns[2]:'size'}, inplace=True)
```

（18）取某一行的唯一实体

下面代码将取「name」行的唯一实体：

```
df["name"].unique()
```

（19）访问子 DataFrame

以下代码将从 DataFrame 中抽取选定了的行「name」和「size」：

```
new_df = df[["name", "size"]]
```

（20）总结数据信息

```python
# Sum of values in a data frame
df.sum()
# Lowest value of a data frame
df.min()
# Highest value
df.max()
# Index of the lowest value
df.idxmin()
# Index of the highest value
df.idxmax()
# Statistical summary of the data frame, with quartiles, median, etc.
df.describe()
# Average values
df.mean()
# Median values
df.median()
# Correlation between columns
df.corr()
# To get these values for only one column, just select it like this#
df["size"].median()
```

（21）给数据排序

```
df.sort_values(ascending = False)
```

（22）布尔型索引

以下代码将过滤名为「size」的行，并仅显示值等于 5 的行：

```
df[df["size"] == 5]
```

（23）选定特定的值

以下代码将选定「size」列、第一行的值：

```
df.loc([0], ['size'])
```

```python
#取某几列
df.iloc[: , 1:3]	
#取某几行
df.iloc[1:3, :]
```



```python
#修改列的顺序
df=pd.read_csv("FILE.csv")
cols = df.columns.tolist()
daf=df[[cols[0],cols[3],cols[1],cols[2]]]
```

