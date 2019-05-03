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
```
# Generator
*杨辉三角*
```
def triangle():
    t = [1]
    while ture:
        yield(t)
        t = [1] + [t[n]+t[n+1] for n in range(len(L)-1)] + [1]
    pass
```    
# Iterable Iterator
* 可以通过iter()函数获得一个Iterator对象
# map/reduce
* map()传入的第一个参数是函数，第二个是iterable, 返回新的iterator
* 因为iterator是惰性的，可以用list来获得一个list
```
reduce(f, [x1, x2, x3]) = f(f((x1, x2), x3)
```
* from functools import reduce
* map()会将函数作用于每一个iterable中，比如‘1234353’，则是将函数分别作用于‘1’‘2’...，再比如['adam', 'LISA', 'barT']
```
# ex.1 利用map()函数，把用户输入的不规范的英文名字，变为首字母大写，其他小写的规范名字。
def normalize(name):
    return name[:1].upper + name[1:].lower # 这里好像把list处理成了[adam]这样的list来调用？
    pass
# 测试
L1 = ['adam', 'LISA', 'barT']
L2 = list(map(normalize, L1))
print(L2)
```
```
# ex.2 prod()函数，求累积
def prod(L):
    return reduce(lambda x,y:x*y , L) lambda为匿名函数，可临时指定一个函数操作
    pass
```
```
# ex.3 将字符串转为浮点数 with reduce & map
return reduce(lambda x, y: x*10 + y, list(map(lambda s: float(s)/1000, s.replace('.',''))))
