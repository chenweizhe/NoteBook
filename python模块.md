### *python模块*

---

> 为了让程序实现起来更方便，将常见的功能组合在一起，按类别分类，使用时直接导入即可
>
> 模块的导入：
>
> ​	import 模块名
>
> ​	from...import..

```python
#!/usr/bin/env python3
import urllib
from urllib import request

data = request.urlopen('https://www.baidu.com').read()
print(len(data))
```

> 自定义模块：除了使用官方提供的模块，还可以使用自定义模块，可以直接写在Python的lib中

```python
import test3
test3.fun()
```

*ps: 函数返回值：简单来说使用return语句，整个函数就成一个值*

