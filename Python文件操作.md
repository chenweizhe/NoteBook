### *Python文件操作*

---

#### 1、文件操作概述

>对于文件的读取，写入，打开，关闭，比如合并多个excel文件

#### 2、文件操作

> 打开或创建文件：open(文件路径,打开方式和进制)
>
> 打开方式：r,w,wb（二进制写入）等
>
> 关闭：close
>
> 写与度：write，read，readline

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
file = open('/home/javazhe/Documents/python_project/python_code/file.txt','w') #创建并打开文件
file2 = open('/home/javazhe/Documents/python_project/python_code/file2.txt','r') #创建并打开文件

data = '我是文件内容'
file.write('我是文件一')

while True:
    line = file2.readline()
    if(len(line) == 0):
        break
    print(line)

# 最后要关闭
file.close()
file2.close()

```

