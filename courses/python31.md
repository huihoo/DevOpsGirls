# 第31课：入门 - 样式风格（六）

一个 Web 应用除了动态语言外，还有图片、样式表等所谓的静态文件，django.contrib.staticfiles 就是干这事的。它将各个应用的静态文件统一收集起来，这样一来，在生产环境中，就会有一个集中便于分发的地方。

### 加个样式表
创建 polls/static/polls/style.css，并添加：
```
li a {
    color: green;
}
```
然后，在 polls/templates/polls/index.html 的文件中添加以下内容：
```
{% load static %}

<link rel="stylesheet" type="text/css" href="{% static 'polls/style.css' %}">
```

### 加个背景
将图片放在 polls/static/polls/images/ 目录下， 

然后在样式表 polls/static/polls/style.css 中添加：
```
body {
    background: white url("images/background.jpg") no-repeat;
}
```
好了，看下效果。 http://localhost:8000/polls/

![class31](images/class31.png)

有背景了，问题的链接变绿了 :)

有关样式表的内容比较多，这块你就自己展开学习了。

配图来自Twitter：@atikix

![配图31](https://wiki.huihoo.com/images/4/40/Devopsgirls31.jpg)
