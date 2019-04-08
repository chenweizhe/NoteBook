### *Python异常处理*

---

#### 1、异常处理概述

> 程序执行过程中，经常碰见异常，如不处理，将导致程序崩溃

#### 2、异常处理

*通过try...except...语句块进行处理*

```python
#!/usr/bin/env python3
try:
    print('My')
    printsss('hi')
except Exception as e:
    print(e)
    print('hello')
```

*输出结果：*

>My
>name 'printsss' is not defined
>hello

