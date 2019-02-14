# 第44课：验证

### 验证器
验证器是可调用（callable）的，它接受一个值并在不符合某些条件时引发ValidationError，验证器可在不同类型的字段之间重用这些验证逻辑。

例如，只允许偶数的验证器：
```
from django.core.exceptions import ValidationError
from django.utils.translation import gettext_lazy as _

def validate_even(value):
    if value % 2 != 0:
        raise ValidationError(
            _('%(value)s is not an even number'),
            params={'value': value},
        )
```
之后 ，你就可以通过字段的 validators 参数将其添加到模型字段的验证中了：
```
from django.db import models

class MyModel(models.Model):
    even_field = models.IntegerField(validators=[validate_even])
```

### 内置验证器
django.core.validators 模块包含一组可调用的验证器，用于模型和表单字段。
* RegexValidator
* EmailValidator
* URLValidator
* validate_email # EmailValidator实例（instance），无任何自定义。   
* validate_slug # RegexValidator实例，用于确保一个值仅包含字母，数字，下划线或连字符。
* validate_unicode_slug # RegexValidator实例，用于确保一个值仅包含Unicode字母，数字，下划线或连字符。
* validate_ipv4_address # RegexValidator实例，用于确保这是一个IPv4地址。
* validate_ipv6_address # 使用 django.utils.ipv6 检查IPv6地址的有效性。
* validate_ipv46_address # 使用 validate_ipv4_address 和 validate_ipv6_address 确保值是有效的IPv4或IPv6地址。
* validate_comma_separated_integer_list # RegexValidator实例，确保值是以逗号分隔的整数列表。
* int_list_validator # 返回一个 RegexValidator 实例，该实例确保字符串由 sep（sep=',')分隔的整数组成。当 allow_negative 为 True 时，允许负整数。
* MaxValueValidator # 若 value 大于 limit_value，则使用 ‘max_value’ 抛出 ValidationError。
* MinValueValidator # 若 value 小于 limit_value，则使用 'min_value' 抛出 ValidationError。
* MaxLengthValidator # 若 value 的长度大于 limit_value，则使用 ‘max_length’ 抛出 ValidationError。
* MinLengthValidator # 若 value 的长度小于 limit_value，则使用 'min_length' 抛出 ValidationError。
* DecimalValidator # 这些 max_digits、max_decimal_places、max_whole_digits 代码可能会抛出 ValidationError 错误。
* FileExtensionValidator # 若在 allowed_extensions 中找不到 value.name 的扩展名，则抛出 ValidationError 错误。
* validate_image_file_extension # 使用 Pillow 确保 value.name 是个有效图像扩展名。
* ProhibitNullCharactersValidator # 若 str（value）包含一个或多个空值字符（'\ x00'），则抛出 ValidationError 错误。  

### URLValidator例子
```
>>> from django.core.validators import URLValidator
>>> from django.core.exceptions import ValidationError
>>> def is_valid_url(url):
...     validate = URLValidator()
...     try:
...         validate(url)
...         return True
...     except ValidationError:
...         return False
... 
>>> is_valid_url("htps://github.com")
False
>>> is_valid_url("https://github.com")
True
```

配图来自Twitter：@ukiukisoda

![配图44](https://wiki.huihoo.com/images/thumb/9/9c/Devopsgirls44.jpg/732px-Devopsgirls44.jpg)

