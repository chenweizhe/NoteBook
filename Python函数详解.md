### *Python函数详解*

---

> 函数的本质就是功能的封装，提高编程的效率和程序的可读性

#### 1、局部变量和全局变量

> 根据作用域的不同定义

```python
# 作用域
i = 10 #全局变量
def fun():
    j = 1 #局部变量
    global k = 10 #在函数里将变量声明为全局变量，通过global
    j+=1
    print(j)

print(i)
fun()
print(k)
```

#### 2、函数使用

> 1、函数的定义：用def 定义函数体通过缩进来体现
>
> 2、函数的调用：直接调用

```python
def abc():
    print('abc');
abc()
```

> 3、函数参数的使用： 定义时的参数为形参，调用时使用的参数为实参

```python
# 形参和实参
def func1(a,b): #a,b为形参
    print(a+b)
    if(a>b):
        print(a)
    else:
        print(b)

func1(3,4) #3,4为实参
```



