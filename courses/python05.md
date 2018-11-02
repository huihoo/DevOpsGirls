# 第5课：条件

将以下内容以Jupyter Notebook的方式做练习和自己总结，可存档附件到作业后面。 

条件：if - elif - else，每个后面跟冒号：
注意：python没有switch – case语句

常用的操作符
```
 <	小于
 <=	小于或等于
 >	大于
 >=	大于或等于
 ==	等于
 !=	不等于
```

创建 test05.py
```
 #!/anaconda3/bin/python3
 import random

 x = random.choice(range(10))
 y = random.choice(range(20))

 if x > y:
    print('x:', x)
 elif x == y:
    print('x = y =', x)
 else:
    print('y:', y)
```

python3 test05.py
```
if - elif - else可嵌套，类似这样：
 if 条件1:
     语句
     if 条件2:
         语句
     elif 条件3:
         语句
     else:
         语句
 elif 条件4:
     语句
 else:
```
一组有趣的例子：条件为真或为假

1、条件为真：不为0、为True、为”None”
```
 >>> a = 1
 >>> if a:
 ...     print("True")
 ... else:
 ...     print("False")
 ...
 True

 >>> a = "None"
 >>> if a:
 ...     print("True")
 ... else:
 ...     print("False")
 ...
 True
```
2、条件为假：为0、为False、为None
```
 >>> a = 0
 >>> if a:
 ...     print("True")
 ... else:
 ...     print("False")
 ...
 False

 >>> a = None
 >>> if a:
 ...     print("True")
 ... else:
 ...     print("False")
 ...
 False
```
你再试试 a = True 或 False的情况。

有点困了，该睡觉了。月亮

配图来自Twitter：@atikix

![配图](https://wiki.huihoo.com/images/f/fe/Devopsgirls05.jpg)