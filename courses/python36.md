# 第36课：视图（二）

这里我们介绍基于类的视图。

### 基于类的视图（Class-based views）
视图不仅仅只有函数（def），而可以是类（class）

基于类的视图提供了另一种将视图实现为Python对象而不是函数的方法。

Django 也提供了一些可用作视图的类的示例，允许你通过继承和复用构建自己的视图并且复用这些代码。

将一个函数定义的视图转换成基于类的视图：

函数定义的视图
```
from django.http import HttpResponse

def my_view(request):
    if request.method == 'GET':
        # <view logic>
        return HttpResponse('result')
```
转换成 -> 基于类的视图：
```
from django.http import HttpResponse
from django.views import View

class MyView(View):
    def get(self, request):
        # <view logic>
        return HttpResponse('result')
```

### 内置基于类的视图
大致的一个划分：
* Base views
* Generic display views
* Generic editing views
* Generic date views
* Class-based views mixins
* Class-based generic views 

配图来自Twitter：@chengr28

![配图36](https://wiki.huihoo.com/images/c/c2/Devopsgirls36.jpg)
