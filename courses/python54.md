# 第54课：Python面试

Python 面试或许会有点像考试，想想之前的中考、高考，你也应该有些感受。

首先，多做Python练习题和编码，重点难点反复推敲理解、做到举一反三。

努力达成的结果，两个字总结：快（基础扎实、编码快）深（重点难点的深入理解，如：模型）

### Python面试题
网上已有很多 Python 面试题了，这里先收集整理一些，反复看和练习，最好把它们记住：
* [关于Python的面试题](https://github.com/taizilongxu/interview_python)
* [2018年最常见的Python面试题&答案（上篇）](https://juejin.im/post/5b6bc1d16fb9a04f9c43edc3) [（下篇）](https://juejin.im/post/5b8505b6e51d4538884d22bf)
* [Python面试必须要看的15个问题](http://codingpy.com/article/essential-python-interview-questions/)

### 问题深入展开
这里就从模型入手，作为一个参考，将你对模型深入理解的思路、重点逐步展开：
* 1、Python 中的一切都是对象。
* 2、模型是一种特殊的对象，它保存在数据库中，列（字段）行（数据）。
* 3、$ python manage.py startapp blog 创建一个应用，生成模型文件：models.py
* 4、在 modles.py 中定义 Post 模型，有标题、内容、创建时间、作者等类变量，它们对应数据库表字段
* 5、激活迁移模型，这时数据库和表会从模型自动生成
* 6、以后表修改就采用类似的步骤：改变模型、生成迁移文件、完成数据库迁移          


配图来自Twitter：@atikix

![配图54](https://wiki.huihoo.com/images/d/d3/Devopsgirls54.jpg)
