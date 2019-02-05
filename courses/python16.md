# 第16课：模块/库（Module/Library）（一）

先抛出一个简单python web应用的例子的目录结构：

```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
    polls/
        __init__.py
        admin.py
        migrations/
            __init__.py
            0001_initial.py
        models.py
        static/
            polls/
                images/
                    background.gif
                style.css
        templates/
            polls/
                detail.html
                index.html
                results.html
        tests.py
        urls.py
        views.py
    templates/
        admin/
            base_site.html
```

### 命名空间（namespace）和作用域（scope）
python最大特点也是最核心思想就是： 一切皆对象。

命名空间是名字和对象的映射，可以把一个namespace理解为一个字典。

命名空间的作用：程序在直接访问变量时，会在当前的命名空间内查找，并会从内到外依次访问所有的作用域直到找到。

命名空间可以分为三类：
* 函数的局部命名空间
* 模块的全局命名空间
* 内置命名空间

作用域就是一个Python程序可以直接访问命名空间的区域，可以具体分为以下四个作用域：
* Local(innermost) 最里面的局部作用域
* Enclosing 外层函数的局部作用域
* Global(next-to-last) 模块的全局作用域
* Built-in(outtermost) 包含Python内置对象的最外层作用域

```
def scope_test():
    def do_local():
        variable = "local variable"

    def do_nonlocal():
        nonlocal variable
        variable = "nonlocal variable"

    def do_global():
        global variable
        variable = "global variable"

    variable = "test variable"
    do_local()
    print("After local assignment:", variable)
    do_nonlocal()
    print("After nonlocal assignment:", variable)
    do_global()
    print("After global assignment:", variable)

scope_test()
print("In global scope:", variable)
```

### 模块
模块即一个Python文件.py

### 包
包是由一系列模块组成的集合，包中必须至少含有一个__init__.py文件，该文件的内容可以为空，用于标识当前文件夹是一个包。

上面例子包含了三个包：mysite、polls、migrations

### 标准模块
Python内置了非常多的模块，大部分是纯Python的，也有一些用C编写的模块。熟练使用这些模块，能帮助你解决日常编程中出现的许多问题，所以大家很有必要熟悉这些标准库模块。

这里简单介绍下以下常用模块的使用方法：
#### error
捕获各种异常，并做特殊处理。

```
>>>import os
>>>os.kill(123, 0)
>>>os.strerror(3)
```
#### subprocess
subprocess模块允许你生成新进程，连接到它们的input/output/error管道，并获取它们的返回代码， 该模块旨在替换几个较旧的模块和功能：os.system、os.spawn*、os.popen*等
```
>>> import subprocess
>>> subprocess.run(["ls", "-l", "/dev/null"], stdout=subprocess.PIPE)
CompletedProcess(args=['ls', '-l', '/dev/null'], returncode=0, stdout=b'crw-rw-rw-  1 root  wheel    3,   2  2  5 17:52 /dev/null\n')
```

#### contextlib
Python程序通过上下文管理能让代码的可读性更强并且错误更少。
```
from contextlib import contextmanager

@contextmanager
def tag(name):
    print("<%s>" % name)
    yield
    print("</%s>" % name)

with tag("h1"):
    print("python")
```

#### glob
glob是用来匹配UNIX风格路径名的模块，支持 '*'、'?'、'[]'三种通配符。
```
$ ls
1.txt	2.txt	a1.txt	a2.txt	b1.txt	b2.txt

>>> import glob
>>> glob.glob('./*.txt')
['./a1.txt', './a2.txt', './b2.txt', './2.txt', './b1.txt', './1.txt']
>>> glob.glob('./a?.txt')
['./a1.txt', './a2.txt']
>>> glob.glob('./b?.txt')
['./b2.txt', './b1.txt']
>>> glob.glob('./[0-9].*')
['./2.txt', './1.txt']
>>> glob.glob('./a[0-9].*')
['./a1.txt', './a2.txt']
>>> glob.glob('./b[0-9].*')
['./b2.txt', './b1.txt']
```

#### operator
标准运算符作为函数，如求和我们可以使用sum，乘积可结合operator和reduce模块来实现。

```
>>> import operator
>>> from functools import reduce
>>> reduce(operator.mul, (5, 4, 3, 2, 1))
120
```

#### functools
functools模块用于高阶函数，包含了一系列操作其它函数的工具。
```
>>> from functools import partial
>>> basetwo = partial(int, base=2)
>>> basetwo.__doc__ = '将base 2字符串转换为整数'        
>>> basetwo('10010')
18
>>> basetwo('11111')
31
```

#### collections
回忆一下之前提到的标准数据类型中包含的：dict, list, set, tuple。

collections模块实现了专门的容器数据类型：
* namedtuple：能创建可以通过属性访问元素内容的扩展元祖。
* deque：一个双端队列，能够在队列两端添加或删除队列元素。
* ChainMap：
* Counter：一个方便、快速计算的计时器工具。
* OrderedDict：Python的dict是无序的，而OrderedDict保证字典健值对的顺序。
* defaultdict：简化了处理不存在键的场景。
* UserDict：
* UserList：
* UserString：

举一个Counter的例子
```
>>> import collections
>>> words = ['a', 'b', 'a', 'c', 'd', 'c', 'e', 'b']
>>> cnt = collections.Counter(words)
>>> cnt.most_common(5)
[('a', 2), ('b', 2), ('c', 2), ('d', 1), ('e', 1)]
```

### 标准库思维导图
7张Python[常见标准库思维导图](https://woaielf.github.io/2018/04/15/python2/)：
* 1、标准库概述
![标准库概述](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/1.png)
* 2、正则表达式
![正则表达式](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/2.png)
* 3、日期 & 时间
![日期 & 时间](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/3.png)
* 4、系统 & 文件
![系统 & 文件](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/4.png)
* 5、进程 & 线程
![进程 & 线程](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/5.png)
* 6、数据库操作
![数据库操作](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/6.png)
* 7、数学运算 & 数据结构
![数学运算 & 数据结构](https://raw.githubusercontent.com/woaielf/woaielf.github.io/master/_posts/media/15237087901003/7.png)

配图来自Twitter：@chengr28

![配图16](https://wiki.huihoo.com/images/b/b9/Devopsgirls16.png)
