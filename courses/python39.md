# 第39课：表单（一）

### 表单
若你的网站需要接收访问者的输入，就需要理解和使用表单。

创建 Form 类时，最重要的是定义表单的字段，以及每个字段的验证逻辑。

Django 提供了一系列的工具和库来帮助您构建表单来接收网站访客的输入，然后处理以及响应这些输入。

### 内置字段
这是一个完整的示例 Form，它为两个字段实现标签，并指定了 auto_id = False 来简化输出：
```
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

### 内置widgets
widget 是 Django 对 HTML 输入元素的表示，widget 处理 HTML 的渲染，以及从与 widget 对应的 GET/POST 字典中提取数据。

一个简单的 widget：Textarea
... 
from django import forms

class CommentForm(forms.Form):
    name = forms.CharField()
    url = forms.URLField()
    comment = forms.CharField(widget=forms.Textarea)
... 

配图来自Twitter：@chengr28

![配图39](https://wiki.huihoo.com/images/thumb/9/9c/Devopsgirls39.jpg/798px-Devopsgirls39.jpg)