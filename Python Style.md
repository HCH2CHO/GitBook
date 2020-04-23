### 标准：

- PEP8    https://www.python.org/dev/peps/pep-0008/#class-names 
- Google Python Style Guide     https://google.github.io/styleguide/pyguide.html#21-lint 



### 方法库：

- pylint：静态代码检查工具
- flake8： 静态代码检查工具
- yapf：代码格式化工具

```
yapf -d <python file>	#前后对比
yapf -i <python file>	#直接修改源文件
```



### 规则屏蔽

```
# pylint: disable=C0325
```

