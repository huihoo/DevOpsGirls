# 第8课：错误、异常

将以下内容以Jupyter Notebook的方式做练习和自己总结，并保存.ipynb。 

本节课涉及一些概念：语法错误、异常、异常处理、抛出异常、自定义异常、Finally始终执行、反向跟踪

注意：错误和异常的区别：
错误（语法错误、解析时）
异常（运行时）

1、语法错误
```
>>> print (Hello World)
  File "<stdin>", line 1
    print (Hello World)
                     ^
SyntaxError: invalid syntax
```

2、异常（运行时）
常见的异常类型：ZeroDivisionError，NameError 和 TypeError
```
>>>1/0
```

3、异常处理（try … except)
```
>>> def zero_fails():
...     x = 1/0
...
>>> try:
...     zero_fails()
... except ZeroDivisionError as err:
...     print('处理运行时错误', err)
```

Python抛出异常相当于：“停止运行这个函数中的代码，将程序执行转到except语句。

raise语句包含以下部分：
* raise关键字；
* 对Exception函数的调用；
* 传递给Exception函数的字符串，包含有用的出错信息。

4、抛出异常（raise）
```
>>> raise Exception('这是一个错误信息')
>>> raise ZeroDivisionError('ZeroFails')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: ZeroFails
```

5、自定义异常，继承自 Exception 类
```
>>>class MyError(Exception):
        def __init__(self, value):
            self.value = value

类 Exception 默认的 __init__() 被覆盖
```

6、Finally
```
>>> try:
...     raise ZeroDivisionError
... finally:
...     print("始终执行")
```

7、traceback

只要抛出的异常没有被处理，Python就会显示反向跟踪，你可将反向跟踪信息写入一个日志文件，让程序继续运行，稍后检查日志文件进行分析。
```
>>> import traceback
>>> try:
...     raise Exception('这是一个错误信息.')
... except:
...     errorFile = open('errorInfo.txt', 'w')
...     errorFile.write(traceback.format_exc())
...     errorFile.close()
...     print('反向跟踪信息写入errorInfo.txt.')
```

其实本课程也包含调试、调试器、断言、断点、日志等内容，我们会在之后的进阶课程逐步展开。

这块有些复杂，多去理解，多看看一些项目里这部分的处理方式。

大部分项目对错误和异常处理都格外重视，会有独立的异常处理模块，如：odoo.exceptions
Search · Exception · GitHub

OK，程序完成调试。

配图来自Twitter：@momoco_haru

![配图8](https://wiki.huihoo.com/images/1/13/Devopsgirls08.png)