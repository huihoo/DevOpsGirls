# 第27课：入门 - 模型和管理后台（二）

涉及到模型，就要使用到数据库。

### 配置数据库
打开 mysite/settings.py 

先创建数据库：mysite
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'mysite',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```
$ python manage.py migrate
```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
```

默认启用以下应用并创建相关数据库表，这些应用给常规项目提供方便：

* django.contrib.admin -- 管理员站点， 你很快就会使用它。
* django.contrib.auth -- 认证授权系统。
* django.contrib.contenttypes -- 内容类型框架。
* django.contrib.sessions -- 会话框架。
* django.contrib.messages -- 消息框架。
* django.contrib.staticfiles -- 管理静态文件的框架。

### 创建模型
定义模型也就是数据库结构设计，数据库和表会从从模型自动生成。Django的迁移代码是由你的模型文件自动生成，它本质上是个历史记录，Django可以用它来进行数据库的滚动更新，通过这种方式使其能够和当前的模型匹配。

编辑 polls/models.py
```
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```
新增Question和Choice两个模型，每个模型被表示为 django.db.models.Model 类的子类。每个模型有一些类变量，它们都表示模型里的一个数据库字段。

使用 ForeignKey 定义了一个关系，每个 Choice 对象都关联到一个 Question 对象。


### 激活模型
修改 mysite/settings.py，增加polls.apps.PollsConfig
```
INSTALLED_APPS = [
    'polls.apps.PollsConfig',
    ...
]
```
$ python manage.py makemigrations polls
```
Migrations for 'polls':
  polls/migrations/0001_initial.py
    - Create model Choice
    - Create model Question
    - Add field question to choice
```
然后执行migrate自动执行数据库迁移并同步管理你的数据库结构。

$ python manage.py sqlmigrate polls 0001
```
BEGIN;
--
-- Create model Choice
--
CREATE TABLE "polls_choice" ("id" serial NOT NULL PRIMARY KEY, "choice_text" varchar(200) NOT NULL, "votes" integer NOT NULL);
--
-- Create model Question
--
CREATE TABLE "polls_question" ("id" serial NOT NULL PRIMARY KEY, "question_text" varchar(200) NOT NULL, "pub_date" timestamp with time zone NOT NULL);
--
-- Add field question to choice
--
ALTER TABLE "polls_choice" ADD COLUMN "question_id" integer NOT NULL;
CREATE INDEX "polls_choice_question_id_c5b4b260" ON "polls_choice" ("question_id");
ALTER TABLE "polls_choice" ADD CONSTRAINT "polls_choice_question_id_c5b4b260_fk_polls_question_id" FOREIGN KEY ("question_id") REFERENCES "polls_question" ("id") DEFERRABLE INITIALLY DEFERRED;
COMMIT;
```
最后，再次运行 migrate 命令，在数据库里创建新定义的模型的数据表，这时就新建了这两张表。

$ python manage.py migrate
```
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, polls, sessions
Running migrations:
  Applying polls.0001_initial... OK
```
所以，改变模型需要这三步：
* 编辑 models.py 文件，改变模型。
* 运行 python manage.py makemigrations 为模型的改变生成迁移文件。
* 运行 python manage.py migrate 来应用数据库迁移。

### Django管理后台
Django会根据模型自动地创建后台界面。

创建一个管理员账号：
```
$ python manage.py createsuperuser
$ python manage.py runserver
http://127.0.0.1:8000/admin/
admin/adminadmin
```

### 将polls应用加入管理
编辑 polls/admin.py 
```
from django.contrib import admin
from .models import Question

admin.site.register(Question)
```
以后其它应用加入管理也采用类似方法，这样就可以在后台统一管理这些应用了。

配图来自Twitter：@atikix

![配图27](https://wiki.huihoo.com/images/8/82/Devopsgirls27.jpg)
