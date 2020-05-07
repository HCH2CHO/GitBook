## Code lay-out 代码布局

#### Indentation 缩进

-  每一级缩进使用4个空格
- 行连接符：\  ()  []  {}
- 挂行缩进方式：
  - ①Aligned with opening delimiter
  - ②Add 4 spaces to distinguish arguments from the rest.
  - ③Hanging indents should add a level

#### 空格是首选的缩进方式

#### 所有行限制的最大字符数为79

#### 在二元运算符之前应该换行

#### Blank Lines 空行

- 顶层函数和类之间空两行
- 类中的方法空一行

#### Source File Encoding 文件编码

 ASCII in Python 2 or UTF-8 in Python 3

#### Imports 导入

- import通常位于文件的顶部，在模块注释和文档字符串之后，在模块的全局变量与常量之前
- import分组：标准库、第三方库、本地库，并在每一分组间加入空行
- 推荐使用绝对路径导入: from ... import ... 
- 避免使用 from ... import * 

#### String Quotes 字符串引号

- 单引号和双引号字符串是相同的 
- 当一个字符串中包含单引号或者双引号字符的时候，使用和最外层不同的符号来避免使用反斜杠

## Whitespace in Expressions and Statements 表达式和语句中的空格

- 避免使用无用的空格

- 避免在尾部添加空格

- 总是在二元运算符两边加一个空格

- 如果使用具有不同优先级的运算符，考虑在具有最低优先级的运算符周围添加空格

- 函数功能注释符号  “:”   “ ->”加空格

  ```
  def munge(input: AnyStr = 1)-> PosInt: 
  	...
  ```

- 利用“="进行函数中参数赋值时不需要加空格

## Comments 注释

- 及时更新代码注释

- 使用完整的句子

- block comments块注释使用一个#和空格开头

- 有节制的使用inline comments行内注释

- Documentation Strings文档字符串

  - 要为所有的公共模块，函数，类以及方法编写文档说明
  - 对于单行的文档说明，尾部的三引号应该和文档在同一行

  ```python
  def complex(real=0.0, imag=0.0):
      """Form a complex number.
  
      Keyword arguments:
      real -- the real part (default 0.0)
      imag -- the imaginary part (default 0.0)
      """
  ```

## Naming Conventions 命名规范

#### Naming Styles

- CamelCase
- camelCase
- snake_case
- lowercase
- UPPERCASE
- UPPER_CASE_WITH_UNDERSCORES

#### Naming Conventions

- 包名和模块名：snake_case、lowercase
- 类名：CamelCase。类内部变量： lowercase
- 异常名： CamelCase+Error
- 全局变量名：snake_case、lowercase
- 函数名和变量名：snake_case、lowercase
- 函数参数和方法参数：lowercase、snake_case。self为实例方法第一个参数，clf为类方法第一个参数；不要与已有关键字冲突，可加一个后缀下划线。
- 方法名和实例变量：snake_case
- 常量：UPPER_CASE_WITH_UNDERSCORES、UPPERCASE
- 下划线

| 模式               | 举例    | 含义                                                         |
| ------------------ | ------- | ------------------------------------------------------------ |
| 单前导下划线       | _var    | 命名约定，仅供类或函数内部使用。通常不会由python解释器强制执行，只作为对程序员的提示 |
| 单末尾下划线       | var_    | 按约定使用以避免与python关键字的命名冲突                     |
| 双前导下划线       | __var   | 当在类上下文中使用时，触发名称修饰。可内部使用，在外部使用时表示为"_类名__var" |
| 双前导和末尾下划线 | __var__ | dunder，表示python语言定义的特殊方法。避免在自己的属性中使用该命名方案 |

## Programming Recommendations

- 和单例对象例如None比较的时候用is / is not，而不是==

- 用def代替lambda

- 将异常抛出，让用户知道有异常发生

  ```
  try:
      process_data()
  except Exception as exc:
      raise DataProcessingFailedError(str(exc))
  ```

- 当代码片段局部使用了某个资源的时候，使用with 表达式来确保这个资源使用完后被清理干净

- 返回的语句保持一致。 函数中的返回语句都应该返回一个表达式，或者都不返回。 没有值的时候使用return None显式指明

- 使用 ”.startswith() 和 ”.endswith() 代替通过字符串切割的方法去检查前缀和后缀

- 对象类型的比较应该用isinstance()而不是直接用type()。isinstance()会将子类和父类认为是同一类型。

- 对于string、list、tuple、dict等序列对象，用判断是否为false的方法来确定是否为空，代替len()

- 不要用 == 去和True或者False比较。正确写法`if greeting: `

- 不要在try...finally...语句中使用return/break/continue.因为在return/break/continue之前，finally部分会被先执行。

## Function Annotations功能标注

```python
def func(a: 'spam' = 4, b: (1, 10) = 5, c: float = 6) -> int:
	return a + b + c
```

## Variable Annotations变量标注

```python
code: int

class Point:
    coords: Tuple[int, int]
    label: str = '<unknown>'
```

