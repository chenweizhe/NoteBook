### *Python控制流*

---

> Python中有3种基本控制流
>
> 1、顺序结构
>
> 2、条件分支结构
>
> 3、循环结构



#### if语句

```
a = 1
if(a == 7):
    print(a)
elif a == 1:
    a += 1
    print(a)
else:
    print('nnnnn',a)
```

#### while语句

```
a= 0
while(a<8):
    print(a,' hello',a+1)
    a+=1
```

#### for语句

```
# 遍历列表
a = ['a','c','b','d'];
for i in a :
    print(i)
# 循环遍历
for i in range(0,8):
    print(i,'hello')
```

#### 中断结构

> 中断结构，指的是中途退出的一种结构，一般是break和continue语句

```
# 中断一次循环，使用continue语句，中断一个循环，使用break
for i in range(8):
    if i ==6:
        continue;
    print(i)
    
for i in range(8):
    if i ==6:
        break
    print(i)
```



#### 实战：输出乘法口诀

```python
for i in range(1,10):
    for j in range(1,i+1):
        # end = ''控制不换行
        print(i,'*',j,'=',i*j,' ',end = '') 
        # print(str(i)+'*'+str(j)+'='+str(i*j))
    print()
    
#逆向输出

for i in range(9,0,-1):
    for j in range(i,0,-1):
        # print(i,'*',j,'=',i*j,' ',end = '')
        print(str(i)+'*'+str(j)+'='+str(i*j)+' ',end='')
    print()    
```

