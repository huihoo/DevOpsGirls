# 第39课：表单（一）

### 表单
若你的网站需要接收访问者的输入，就需要理解和使用表单。

Django 提供了一系列的工具和库来帮助您构建表单来接收网站访客的输入，然后处理以及响应这些输入。

### 内置字段
```
>>> from django.core.wsgi import get_wsgi_application
>>> application = get_wsgi_application()

>>> from django import forms
>>> class CommentForm(forms.Form):
...     name = forms.CharField(initial='Allen')
...     url = forms.URLField(initial='https://huihoo.com')
...     comment = forms.CharField()
... 
>>> f = CommentForm(auto_id=False)
>>> print(f)
<tr><th>Name:</th><td><input type="text" name="name" value="Allen" required></td></tr>
<tr><th>Url:</th><td><input type="url" name="url" value="https://huihoo.com" required></td></tr>
<tr><th>Comment:</th><td><input type="text" name="comment" required></td></tr>
```

### 

配图来自Twitter：@chengr28

![配图39](https://wiki.huihoo.com/images/thumb/9/9c/Devopsgirls39.jpg/798px-Devopsgirls39.jpg)