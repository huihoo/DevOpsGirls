# 第47课：日志

Django 使用 Python 内置的 logging 模块处理日志信息。

### 日志框架
一个 Python logging 配置有以下四个部分组成：
* Loggers
* Handlers
* Filters
* Formatters

#### Loggers
logger 是日志系统的入口。每个 logger 都是命名的 bucket， 消息写入 bucket 以便进一步处理。

日志级别
* logger.debug()
* logger.info()
* logger.warning()
* logger.error()
* logger.critical()

此外，你还可以：
* logger.log()：手动输出一条指定日志级别的日志消息。
* logger.exception()：创建一个包含当前异常堆栈帧的 ERROR 级别日志消息。

#### Handlers
Handler 是决定如何处理 logger 中每一条消息的引擎。它描述特定的日志行为，比如把消息输出到屏幕、文件或网络 socket。

#### Filters
在日志记录从 logger 传到 handler 的过程中，使用 Filter 来做过滤操作。

#### Formatters
日志记录最终是以文本呈现，Formatter 描述文本的格式。

### 配置示例
一个简单的配置，将来自 Django logger 的所有日志记录写入本地文件：
```
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'handlers': {
        'file': {
            'level': 'DEBUG',
            'class': 'logging.FileHandler',
            'filename': '/var/log/django/debug.log',
        },
    },
    'loggers': {
        'django': {
            'handlers': ['file'],
            'level': 'DEBUG',
            'propagate': True,
        },
    },
}
```

### 使用Logger
配置好了 logger，handler，filter 和 formatter 后，就是在代码里调用 logging 模块：
```
import logging

logger = logging.getLogger(__name__)

def my_view(request, arg1, arg):
    ...
    if bad_mojo:
        logger.error('Something went wrong!')
```
bad_mojo 条件每次满足都会写一条 error 日志。

配图来自Twitter：@tomo_3

![配图47](https://wiki.huihoo.com/images/c/ce/Devopsgirls47.jpg)