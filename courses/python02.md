
# 第2课：快速熟悉Python

* 一行Python代码，Hello World
* 了解整数、浮点数、字符串、布尔值
* 了解变量、关键字、变量命名规范

运行Anaconda下的Jupyter，完成以下的一些操作：

### （1）hello world
`print “Hello World” `

能运行吗？若不行，请搜索并完成正确print打印。
注意：我们现在使用的是Python3。

### （2）数据类型
```
counter = 100   # 整型变量
miles   = 100.0   # 浮点型变量
a, b = 1, 2 # 多个变量赋值
name = “Python”   # 字符串

true, false # 布尔值

print (counter)
print (miles)
print (name)

print(type(name))
isinstance(name, str)
```

### （3）类型转换
```
整数 ->  浮点数
a = 12
b = float(a)
a
b

浮点数 -> 整数
c = 12.0
d = int(c)
c 
d
```

扩展练习：其它类型的相互转换。

### （4）关键字
关键字即保留字，我们不能把它们用作任何标识符命名。

Python关键字有哪些？
```
import keyword
keyword.kwlist
```
然后记住它们

### （5）一些命名规范：
* a、必须以一个字母或一个下划线字符开头；
* b、字母可以是大小写，但大小写是不同的，如：Ax不同于aX；
* c、数字可以是从0到9的任意数字。

合法变量名：
* my_answer
* answer12
* answer_12
* YourAnswer

不合法变量名：
* 12answer（不能以数字开头）
* your-answer（不允许连字符）
* my answer （不允许有空格）

### （6）
作业2:type()和isinstance()的区别

运行下看系统给出的一些信息：
```
a = 100
print(type(a)

b = 101
isinstance(b, int)
```
搜索整理出区别点和关系。

最后，可小结和总结下（1-5) 知识点和Jupyter操作截图 + (6)的作业一起提交作业。

配图来自Twitter：@MacciattoS2

![配图1](https://wiki.huihoo.com/images/8/80/Devopsgrils02.jpg)