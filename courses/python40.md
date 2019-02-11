# 第40课：表单（二）

### 模型表单
模型中定义了字段，表单中就不需要再定义字段类型了。每个模型字段都有一个对应的默认表单字段。

Django 提供了一个辅助类让你可以从一个 Django 模型创建一个 Form 类。
```
>>> from django.forms import ModelForm
>>> from polls.models import Person
>>> class PersonForm(ModelForm):
...     class Meta:
...         model = Person
...         fields = ['first_name', 'last_name']
... 
>>> form = PersonForm('Jeff', 'Zhang')
```
思考下，如何把这条记录写入(save)数据库中。

### 表单集
formset是一个抽象层，它可以在同一页面上处理多个表单。

如一次创建多个Person，需要创建 PersonForm 的 formset，方法如下：
```
>>> from django.forms import formset_factory
>>> PersonFormSet = formset_factory(PersonForm)
>>> formset = PersonFormSet()
>>> for form in formset:
...     print(form.as_table())
... 
<tr><th><label for="id_form-0-first_name">First name:</label></th><td><input type="text" name="form-0-first_name" maxlength="30" id="id_form-0-first_name"></td></tr>
<tr><th><label for="id_form-0-last_name">Last name:</label></th><td><input type="text" name="form-0-last_name" maxlength="30" id="id_form-0-last_name"></td></tr>
```
### 字段验证
Django 表单（和模型）字段支持使用简单的实用函数和称为验证器的类。验证器只是一个可调用的对象或函数，它接受一个值，如果值有效则返回任何内容，否则引发 ValidationError。 

这些可以通过字段的验证器参数传递给字段的构造函数，或者使用 default_validators 属性定义在 Field 类上。

SlugField 是一个带有自定义验证器的 CharField，用于验证提交的文本是否符合某些字符规则。
```
>>> from django.core import validators
>>> from django.forms import CharField
>>> 
>>> class SlugField(CharField):
...     default_validators = [validators.validate_slug]
... 
>>> slug = forms.SlugField() 
```
  
配图来自Twitter：@chengr28

![配图40](https://wiki.huihoo.com/images/thumb/1/16/Devopsgirls40.jpg/768px-Devopsgirls40.jpg)

