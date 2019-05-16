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
```
# filter
* filter()也接收一个函数和一个序列。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素
* Python strip() 方法用于移除字符串**头尾**指定的字符（默认为空格或换行符）或字符序列
* return n % 2 == 1 右边为判断语句，返回值为True or False
## b = a[i:j:s]
> b = a[i:j:s]这种格式呢，i,j与上面的一样，但s表示步进，缺省为1.
所以a[i:j:1]相当于a[i:j]
当s<0时，i缺省时，默认为-1. j缺省时，默认为-len(a)-1
所以a[::-1]相当于 a[-1:-len(a):-1]，也就是从最后一个元素到第一个元素复制一遍。所以你看到一个倒序的。
# sorted
* sorted([36, 5, -12, 9, -21], key=abs) key指定的函数将作用于list的每一个元素上，并根据key函数返回的结果进行排序
> 要进行反向排序，不必改动key函数，可以传入第三个参数reverse=True
```
# L = [('Bob', 75), ('Adam', 92), ('Bart', 66), ('Lisa', 88)] 
# 将L从大按姓名排序，按成绩排序
def by_name(t):
    return t[0]
    pass
L2 = sorted(L, key = by_name)
print(L2)

def = by_score(t):
    return -t[1]
    pass
L2 = sorted(L, key = by_score)
print(L2)
```
# 返回函数
> 另一个需要注意的问题是，返回的函数并没有立刻执行，而是直到调用了f()才执行.
> 每次调用都会返回一个新的函数
# 匿名函数: 
* lambda x: x * x 
