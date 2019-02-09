# 第28课：入门 - 视图和模板（三）

### 视图
Django 中的视图的概念是一类具有相同功能和模板的网页的集合，如大家熟悉的博客会包含以下视图：
* 博客首页：展示最近的几条博客
* 详情页
* 评论
* 归档页：以年、月、日为单位的归档博客

在我们的投票(Polls)应用中，需要以下视图：
* 问题索引页：显示最近的几个投票问题。
* 问题详情页：显示某个投票的问题和不带结果的选项列表。
* 问题结果页：显示某个投票的结果。
* 投票处理器：用于响应用户为某个问题的特定选项投票的操作。

为了将 URL 和视图关联起来，Django 使用了 'URLconfs' 来配置，URLconf 将 URL模式（urlpatterns）映射到视图。

现在我们往 polls/views.py 里添加以下新视图：
```
def detail(request, question_id):
    return HttpResponse("你看到的问题是 %s." % question_id)

def results(request, question_id):
    response = "你看到的问题结果是 %s."
    return HttpResponse(response % question_id)

def vote(request, question_id):
    return HttpResponse("你在此问题上的投票 %s." % question_id)
```

编辑 polls/urls.py，添加几个 url() 函数调用：
```
from django.urls import path

from . import views

urlpatterns = [
    # ex: /polls/
    path('', views.index, name='index'),
    # ex: /polls/5/
    path('<int:question_id>/', views.detail, name='detail'),
    # ex: /polls/5/results/
    path('<int:question_id>/results/', views.results, name='results'),
    # ex: /polls/5/vote/
    path('<int:question_id>/vote/', views.vote, name='vote'),
]
```

### 模版
使用模版，我们可以不用把页面的设计写死在视图函数的代码里，而是将页面的设计从代码中分离出来，方便今后的维护。

我们创建 polls/templates/polls 目录，然后创建 index.html，因为这样 Django 能找到对应的 app_directories，这样使用 polls/index.html 就可以引用此模版了，把模版放到各自的命名空间下是个好习惯。

编辑 polls/templates/polls/index.html
```
{% if latest_question_list %}
    <ul>
    {% for question in latest_question_list %}
        <li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
    {% endfor %}
    </ul>
{% else %}
    <p>没有投票</p>
{% endif %}
```
更新一下 polls/views.py 里的 index 视图来使用此模板，使用 render() 重写 index() 视图，而不是使用HttpResponse() ：
```
from django.http import HttpResponse
from django.shortcuts import render
from .models import Question

def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    context = {'latest_question_list': latest_question_list}
    return render(request, 'polls/index.html', context)
```

$ python manage.py runserver

打开 http://localhost:8000/admin/ 添加几个问题：
* 问题一
* 问题二
* 问题三

再打开 http://localhost:8000/polls/ 你应该可以看见刚创建的三个问题 :)

这样，我们就初步学习了视图创建和模版使用的基础知识了。

配图来自Twitter：@atikix

![配图28](https://wiki.huihoo.com/images/3/30/Devopsgirls28.jpg)
