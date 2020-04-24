### 标准：

- PEP8

https://www.python.org/dev/peps/pep-0008/#class-names 

- Google Python Style Guide

https://google.github.io/styleguide/pyguide.html#21-lint 

https://zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/contents/ 

### 方法库：

- pylint：静态代码检查工具
- flake8： 静态代码检查工具
- yapf：代码格式化工具

```
yapf -d <python file>	#前后对比
yapf -i <python file>	#直接修改源文件
```

pylint   在用户目录下创建.pylintrc，写法参考https://github.com/PyCQA/pylint/blob/master/pylintrc 

yapf/yapflib/style.py 中可修改PEP8的COLUMN_LIMIT 最大字符限度

### 规则屏蔽

```
# pylint: disable=C0325
```



研读：

 https://www.cnblogs.com/Rohn/p/10946242.html 

```
EAFP优于LBYL
It's Easier to Ask for Forgiveness than Permisision.
Look Befor You Leap.
LBYL:防御性的代码跟业务逻辑混在一块降低了可读性。利用try...excet做异常处理，而不是条件判断
```

使用enumerate进行迭代

```python
fruits = ['orange', 'grape', 'pitaya']
for index,fruit in enumerate(fruits):
	print(index,':',fruit)
```

用生成式生成列表

```python
data = [7, 20, 3, 15, 11]
result = [num *3 for num in data if num >10]
print(result)  # [60, 45,33]
```

用zip组合键和值来创建字典

```python
keys = ['Safe', 'Bob', 'Thomas']
values = ['Hammad', 'Builder', 'Engine']
d = dict(zip(keys,values))
print(d)
```

