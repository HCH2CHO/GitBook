一直想形成一些代码规范，哪怕是自己的代码规范。以为自己还是很乱，却发现潜意识里已经有了点习惯。

```
大驼峰——类
小驼峰——函数
下划线——变量（复杂类型加“_类型”）
```

不过也好，毕竟是个自己适应的习惯。




### 一些经验

- 每个变量宜在函数开始处定义好，不宜在中间定义
- 定义变量时，可使0不代表实际意义，只做初始化
- 避免太多变量控制一个变量的问题，可结合二分法的思想，划分为多个变量，便于问题追踪。回想中移重庆项目
- 可修改的变量及文件路径,宜写在配置文件中
- 在循环体中，如需对某一响应变量进行一次运算，可在运算后将其清空，根据是否为空判断是否再运算。


