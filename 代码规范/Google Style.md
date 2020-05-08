## Python语言规范

### 2.1 Lint

设置一个行注释来抑制警告，推荐使用符号名来标识，如

```
# pylint:disable=C0112
# pylint:disable=empty-docstring
```

你可以使用命令 `pylint --list-msgs` 来获取pylint告警列表. 你可以使用命令 `pylint --help-msg=C6409` , 以获取关于特定消息的更多信息. 

### 2.2 import

使用 `import x` 来导入包和模块.

使用 `from x import y` , 其中x是包前缀, y是不带前缀的模块名.

使用 `from x import y as z`, 如果两个要导入的模块都叫做y或者y太长了.

导入时不要使用相对名称. 即使模块在同一个包中, 也要使用完整包名. 这能帮助你避免无意间导入一个包两次. 

### 2.14 True/False Evaluations判断

Python在布尔上下文中会将某些值求值为false. 按简单的直觉来讲, 就是所有的”空”值都被认为是false. 因此0， None, [], {}, “” 都被认为是false. 

- 尽可能使用隐式的false。

- 永远不要用==或者!=来比较单件, 比如None/False/True. 使用is或者is not. 

### 2.15 Deprecated Language Features过时的语言特性

高级循环， 按照从左至右的顺序，分别是外层循环到内层循环

```
[expression for x in X [if condition] 
			for y in Y [if condition] 
			... 
			for n in N [if condition] ]
```

### 2.16 Lexical Scoping词法作用域

Python函数可以引用外层函数中定义的变量, 但是不能够对它们赋值. 对一个块中的某个名称的任何赋值都会导致Python**将对该名称的全部引用当做局部变量**, 甚至是赋值前的处理. 如果碰到global声明, 该名称就会被视作全局变量. 

## Python风格规范

### 3.1分号

不要在行尾加分号, 也不要用分号将两条命令放在同一行.

### 3.2行长度

每行不超过80个字符

使用括号隐式连接

### 3.3括号

不要过多使用括号

### 3.4缩进

用4个空格来缩进代码

### 3.5空行

### 3.6空格

### 3.7Shebang

程序的main文件应该以#!/usr/bin/python3开始.

### 3.8 Comments and Docstrings

-  函数和方法

   一个函数必须要有文档字符串，除非它外部不可见、简洁明了。 文档字符串应该包含函数做什么, 以及输入和输出的详细描述.  关于函数的几个方面应该在特定的小节Args、Returns、Raise中进行描述记录， 这几个方面如下文所述 

  ```python
  def fetch_bigtable_rows(big_table,keys,other_silly_variable=None):
      """Fetches rows from a Bigtable.
  
      Retrieves rows pertaining to the given keys from the Table instance
      represented by big_table.  Silly things may happen if
      other_silly_variable is not None.
  
      Args:
          big_table: An open Bigtable Table instance.
          keys: A sequence of strings representing the key of each table row
              to fetch.
          other_silly_variable: Another optional variable, that has a much
              longer name than the other args, and which does nothing.
  
      Returns:
          A dict mapping keys to the corresponding table row data
          fetched. Each row is represented as a tuple of strings. For
          example:
  
          {'Serak': ('Rigel VII', 'Preparer'),
           'Zim': ('Irk', 'Invader'),
           'Lrrr': ('Omicron Persei 8', 'Emperor')}
  
          If a key from the keys argument is missing from the dictionary,
          then that row was not found in the table.
  
      Raises:
          IOError: An error occurred accessing the bigtable.Table object.
      """
      pass
  ```

- 类

  类应该在其定义下有一个用于描述该类的文档字符串.  如果你的类有公共属性(Attributes), 那么文档中应该有一个属性(Attributes)段.  

  ```python
  class SampleClass(object):
      """Summary of class here.
  
      Longer class information....
      Longer class information....
  
      Attributes:
          likes_spam: A boolean indicating if we like SPAM or not.
          eggs: An integer count of the eggs we have laid.
      """
  
      def __init__(self, likes_spam=False):
          """Inits SampleClass with blah."""
          self.likes_spam = likes_spam
          self.eggs = 0
  
      def public_method(self):
          """Performs operation blah."""
  ```

-  块注释和行注释

  最需要写注释的是代码中那些技巧性的部分. 如果你在下次 代码审查 的时候必须解释一下, 那么你应该现在就给它写注释. 对于复杂的操作, 应该在其操作开始前写上若干行注释. 对于不是一目了然的代码, 应在其行尾添加注释.

  ```python
  # We use a weighted dictionary search to find out where i is in
  # the array.  We extrapolate position based on the largest num
  # in the array and the array size and then do binary search to
  # get the exact number.
  
  if i & (i-1) == 0:        # True if i is 0 or a power of 2.
  ```

### 3.10 Strings

- 使用%、+、format格式化字符串。

```python
x = a + b
x = '%s, %s!' % (imperative, expletive)
x = '{}, {}!'.format(imperative, expletive)
x = 'name: %s; score: %d' % (name, n)
x = 'name: {}; score: {}'.format(name, n)
```

- 避免在循环中用+和+=操作符来累加字符串. 由于字符串是不可变的, 这样做会创建不必要的临时对象, 并且导致二次方而不是线性的运行时间. 作为替代方案, 你可以将每个子串加入列表, 然后在循环结束后用 `.join` 连接列表.  

### 3.11 Files and Sockets

在文件和sockets结束时, 显式的关闭它。除文件外, sockets或其他类似文件的对象在没有必要的情况下打开, 会有许多副作用。

推荐使用“with”语句以管理文件:

```
with open("hello.txt") as hello_file:
    for line in hello_file:
        print line
```

### 3.12 TODO Comments

为临时代码使用TODO注释, 它是一种短期解决方案. 

### 3.13 Imports formatting

### 3.16 Naming

##### Guidelines derived from Guido’s Recommendations

| Type                       | Public             | Internal                                                     |
| -------------------------- | ------------------ | ------------------------------------------------------------ |
| Modules                    | lower_with_under   | _lower_with_under                                            |
| Packages                   | lower_with_under   |                                                              |
| Classes                    | CapWords           | _CapWords                                                    |
| Exceptions                 | CapWords           |                                                              |
| Functions                  | lower_with_under() | _lower_with_under()                                          |
| Global/Class Constants     | CAPS_WITH_UNDER    | _CAPS_WITH_UNDER                                             |
| Global/Class Variables     | lower_with_under   | _lower_with_under                                            |
| Instance Variables         | lower_with_under   | _lower_with_under (protected) or __lower_with_under (private) |
| Method Names               | lower_with_under() | _lower_with_under() (protected) or __lower_with_under() (private) |
| Function/Method Parameters | lower_with_under   |                                                              |
| Local Variables            | lower_with_under   |                                                              |



### 3.18 Function length

函数尽量简短且功能单一，不超过40行。简短的函数更易于管理。

### 3.19 Type Annotations

- 用 \# type: 注释变量类型

```python
a = SomeUndecoratedFunction()  # type: Foo
```

- typing标准库，TypeVar、NewType