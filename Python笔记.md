# 尾递归

> 使用递归函数需要注意防止栈溢出。在计算机中，函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧

> 尾递归是指，在函数返回的时候，调用自身本身，并且，return语句不能包含表达式。这样，编译器或者解释器就可以把尾递归做优化，使递归本身无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。
```
def fact(n):
    return fact_iter(n, 1)
def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product)
```
*练习：汉诺塔（自己写的）*
```
def mov(a, b):
    a, b = b, a
    return a, b
def move(n, a, b, c):
    if n == 1:
        print(a, '-->', c)
    else:
        b, c = mov(b, c)
        move(n-1, a, b, c)
        b, c = mov(b, c)
        move(1, a, b, c)
        a, b = mov(a, b)
        move(n-1, a, b, c)
        a, b = mov(a, b)
A = 'A'
B = 'B'
C = 'C'
```
# 切片
```
>>> 'ABCDEFG'[::2]
'ACEG'
```
*练习：去除字符串首尾的空格（别人写的）*
```
while x[:1] = ' ':
    x[:1] = x[1:]
while x[-1:] = ' ':
    x[-1:] = x[:-1]
    return x
