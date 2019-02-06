# 第20课：元编程（Metaprogramming）
软件开发领域中最经典的口头禅就是“don’t repeat yourself”。 也就是说，任何时候当你的程序中存在很多重复的代码时，我们都应该想想是否有更好的解决方案。在Python当中，通常都可以通过元编程来解决这类问题，主要技术是使用装饰器、类装饰器和元类。

## 在函数上添加包装器

1、定义一个装饰器，增加额外的操作处理(如日志、计时、计数等)，也可定义多个装饰器。

此装饰器是通过@wraps来实现的。

```
import time
from functools import wraps

def timethis(func):
    '''
    装饰器报告执行时间
    '''
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(func.__name__, end-start)
        return result
    return wrapper
```    

2、使用装饰器
```    
>>> @timethis
... def countdown(n):
...     '''
...     计数
...     '''
...     while n > 0:
...         n -= 1
...
>>> countdown(1000)
countdown 5.602836608886719e-05
>>> countdown(10000)
```    
3、解除装饰器
使用__wrapped__解除装饰器
```  
>>> countdown.__wrapped__(1000)
>>> countdown.__wrapped__(10000)
```  
这时就没打印时间信息了

注意：并不是所有的装饰器都使用了 @wraps，如内置的装饰器 @staticmethod 和 @classmethod 就没有遵循这个约定 (它们把原始函数存储在属性 __func__ 中)。 

嗯，有点累了，带狗狗出去散下步。

配图来自Twitter：@chengr28

![配图20](https://wiki.huihoo.com/images/5/5a/Devopsgirls20.jpg)
