# 第18课：接口（Interface）

### 什么是接口
接口只是定义了一组方法，而没有具体实现。

Python的接口由抽象类和抽象方法去实现，接口不能被实例化，只能被别的类继承去实现相应的功能。

### 实现方法
Python 使用 abc（Abstract Base Classes）模块可以轻松的定义抽象基类，抽象类的目的就是让别的类继承它并实现特定的抽象方法。

### 用抽象类和抽象方法实现接口
1、定义抽象基类
```
from abc import ABCMeta,abstractmethod  
  
class interface(object):  
    __metaclass__ = ABCMeta #抽象类  
    @abstractmethod  #抽象方法  
    def python(self):  
        pass      
 
    def rust(self):  
        pass 
```
2、继承基类并实现具体的抽象方法
```
class ImplementationInterfacePython(interface):
    def __init__(self):      
        print ('这是接口实现')  
    def python(self):  
        print ('实现python方法') 
    def rust(self):  
        pass     

class ImplementationInterfaceRust(interface): 
    def __init__(self):      
        print ('这是接口实现')  
    def python(self):  
        pass        
    def rust(self):  
        print ("实现rust方法") 

>>> obj = ImplementationInterfacePython()
这是接口实现
>>> obj.python()
实现python方法
>>> obj = ImplementationInterfaceRust()
这是接口实现
>>> obj.rust()
实现rust方法

```
### 用普通类实现接口
1、定义接口
```
class interface(object):
    def python(self):  
        pass  
      
    def rust(self):  
        pass  

```

2、实现接口
```
class ImplementationInterfacePython(interface):
    def __init__(self):  
        pass  
    def python(self):  
        print ("实现接口中的python方法")  
          
          
class ImplementationInterfaceRust(interface): 
    def __init__(self):  
        pass  
    def rust(self):  
        print ("实现接口中的rust方法")  


>>> obj = ImplementationInterfacePython()
>>> obj.python()
实现接口中的python方法
>>> obj = ImplementationInterfaceRust()
>>> obj.rust()
实现接口中的rust方法
```

### zope.interface
此项目提供了Python对象接口的参考实现，大家可通过此项目扩展学习。

https://pypi.org/project/zope.interface/

配图来自Twitter：@chengr28

![配图17](https://wiki.huihoo.com/images/6/6e/Devopsgirls18.jpg)
