# 第26课：入门 - 请求和响应（一）

### 创建第一个Django应用
注意这里是创建应用而不是创建项目：
* 应用是一个专门做某件事的网络应用程序——比如博客系统，或者简单的投票程序。
* 项目则是一个网站使用的配置和应用的集合。项目可以包含很多个应用。应用可以被很多个项目使用。

进入上一节课创建的 mysite 目录，然后运行：

$ python manage.py startapp polls
```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

### 编写第一个视图
打开 polls/views.py，加入以下代码：
```
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello Polls")
```

### 创建URLconf
新建urls.py，加入以下代码：
```
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

### 修改根URLconf
打开 mysite/urls.py，插入一个include()：
```
from django.contrib import admin
from django.urls import path
from django.conf.urls import include

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]  
```

### 运行应用
$ python manage.py runserver

http://localhost:8000/polls/

浏览器返回：Hello Polls

好了，我们完成了第一个应用创建和请求与响应。

配图来自Twitter：@DSmile9

![配图26](https://wiki.huihoo.com/images/3/30/Devopsgirls26.png)