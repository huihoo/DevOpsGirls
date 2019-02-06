# 第17课：模块/库（Module/Library）（二）

### 编写自己的模块
写一个简单的模块文件，包含两个类，每个类有一个函数。

```
# mymodule.py
class A:
    def python(self):
        print('A.python')

class B(A):
    def julia(self):
        print('B.julia')
```

运行mymodule

```
>>> import mymodule
>>> a = mymodule.A()
>>> a.python()
A.python
>>> b = mymodule.B()
>>> b.julia()
B.julia
```
### 对这个模块文件进行分解
用mymodule目录来替换文件 mymodule.py，创建 a.py、b.py和__init__.py文件。

```
mymodule/
    __init__.py
    a.py
    b.py
```

a.py文件内容
```
# a.py
class A:
    def python(self):
        print('A.python')
```

b.py文件内容
```
# b.py
from .a import A
class B(A):
    def julia(self):
        print('B.julia') 
```        

__init__.py文件内容
```
# __init__.py
from .a import A
from .b import B
```

然后你也试试调用模块与函数。

真正的模块化设计和开发可没这么简单，这里只是让大家先有一个基本的概念。

好吧，今天就先到这，可以放学了 :)

配图来自Twitter：@chengr28

![配图17](https://wiki.huihoo.com/images/6/68/Devopsgirls17.jpg)

