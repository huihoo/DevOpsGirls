# 第41课：认证

### 中间件
中间件是可调用的，它接受请求并返回响应，就像视图一样。

中间件是 Django 请求/响应处理的钩子框架。它是一个轻量级的、低层的插件系统，用于全局改变 Django 的输入或输出。

每个中间件组件负责做一些特定的功能。如，AuthenticationMiddleware 中间件 ，它使用会话将用户与请求关联起来。

一些常见的功能我们可以采用中间件的方式，当然，我们也可以开发新的中间件。

中间件是有顺序的，因为中间件会依赖其他中间件。你可以把它想象成一个洋葱：每个中间件都是一个层，它们覆盖了洋葱的核心。如果请求是通过洋葱的所有层（每一个调用 get_response ）以将请求传递到下一层，一直到内核的视图，那么响应将在返回的过程中通过每个层（以相反的顺序）。

以下是中间件的顺序（ordering）：
* 1、SecurityMiddleware
* 2、UpdateCacheMiddleware
* 3、GZipMiddleware
* 4、SessionMiddleware
* 5、ConditionalGetMiddleware
* 6、LocaleMiddleware
* 7、CommonMiddleware
* 8、CsrfViewMiddleware
* 9、AuthenticationMiddleware
* 10、MessageMiddleware
* 11、FetchFromCacheMiddleware
* 12、FlatpageFallbackMiddleware
* 13、RedirectFallbackMiddleware

### 用户认证
Django带有用户身份验证系统，包含用户账号、用户组、权限和基于cookie的用户管理。

![class41-01](images/class41-01.png)

默认用户的主要属性有：
* username
* password
* email
* first_name
* last_name
![class41-03](images/class41-03.png)

![class41-02](images/class41-02.png)

### 外部身份验证
```
```

配图来自Twitter：@chengr28

![配图41](https://wiki.huihoo.com/images/thumb/3/3e/Devopsgirls41.png/728px-Devopsgirls41.png)
