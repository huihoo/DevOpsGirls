# 第48课：安全概览

在 Web 应用的发展中，安全是最重要主题，Django 提供了多种保护手段和机制。

本节课概述 Django 安全功能，以及 Django 驱动网站的安全建议。

### XSS 保护
Cross site scripting (XSS) 攻击允许恶意用户将客户端脚本注入其他用户的浏览器中，这通常通过让用户单击链接来实现，该链接将导致攻击者的JavaScript由用户的浏览器执行。

使用 Django 模板可以保护你免受大多数XSS攻击，存在一定局限性。

### CSRF 保护
Cross site request forgery (CSRF) 攻击允许恶意用户使用其他用户的证书（credentials）执行操作，而无需用户的知情或同意。

Django 内置了针对大多数类型的CSRF攻击的保护，只要你在适当的地方启用和使用它，也存在一定局限性。

CSRF 通过检查每个POST请求中的 secret 来保护工作，用户可使用 csrf_exempt 装饰器标记视图。

### SQL 注入保护
SQL 注入（injection）是一种攻击类型，恶意用户可以在数据库上执行任意SQL代码，这可能导致数据库记录被删除或数据泄漏。

Django 查询集（querysets）受到SQL注入的保护，它们的查询是使用查询参数化构造的，查询的SQL语句与查询的参数分开定义。由于参数可能是用户提供的，因此不安全，所以它们会被底层数据库驱动程序转义（escaped）。

### 点击劫持保护
点击劫持（Clickjacking）也是一种攻击类型，其中恶意网站将另一个站点包装（wraps）在一个帧中，此攻击可能导致不知情的用户被欺骗在目标站点上执行意外操作。

Django 包含 X-Frame-Options 中间件形式的点击劫持保护，在支持的浏览器中可以防止网站在框架内渲染。 

### SSL/HTTPS
支持 HTTPS 的站点拥有更好的安全性，请尽可能使用它。 

### Header 验证
这个主要是防虚假主机的，因为即使安全配置了的 Web 服务器也容易受到虚假主机 Headers 的影响，Django 会根据 django.http.HttpRequest.get_host() 方法中的 ALLOWED_HOSTS 设置验证主机 Headers。

### Session 安全
这块是有关 [django.contrib.sessions](python42.md) 的主题。

配图来自Twitter：@tomo_3

![配图48](https://wiki.huihoo.com/images/thumb/e/e3/Devopsgirls48.jpg/684px-Devopsgirls48.jpg)
