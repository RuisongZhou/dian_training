# Dian_python学习记录5

## 函数式编程(2)

### 装饰器

在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。

本质上，decorator就是一个返回函数的高阶函数。所以，我们要定义一个能打印日志的decorator，可以定义如下：

```py
# 定义一个函数
>> def now():
...     print('2015-3-25')
...
>>> f = now
>>> f()
2015-3-25

--------------------------------------
# 在不改变now()函数的定义的基础上增强函数功能

def log(func):
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper

观察上面的log，因为它是一个decorator，所以接受一个函数作为参数，并返回一个函数。我们要借助Python的@语法，把decorator置于函数的定义处：


@log
def now():
    print('2015-3-25')
```

调用`now()`函数，不仅会运行`now()`函数本身，还会在运行`now()`函数前打印一行日志：

```py
>>> now()
call now():
2015-3-25
```

把`@log`放到`now()`函数的定义处，相当于执行了语句：

`now = log(now)`

`wrapper()`函数的参数定义是`(*args, **kw)`，因此，`wrapper()`函数可以接受任意参数的调用。在`wrapper()`函数内，首先打印日志，再紧接着调用原始函数。

### 偏函数

Python的`functools`模块提供了很多有用的功能，其中一个就是偏函数（Partial function）。

int()函数可以把字符串转换为整数，当仅传入字符串时，int()函数默认按十进制转换:

```py
>>> int('12345')
12345
```

但int()函数还提供额外的base参数，默认值为10。如果传入base参数，就可以做N进制的转换：

```py
>>> int('12345', base=8)
5349
>>> int('12345', 16)
74565
```

> base参数n指定的是将你的字符串当作n进制来转化为10进制。而不是10进制转化为n进制。

假设要转换大量的二进制字符串，每次都传入`int(x, base=2)`非常麻烦，于是，我们想到，可以定义一个`int2()`的函数，默认把`base=2`传进去：

```py
def int2(x, base=2):
    return int(x, base)
```

`functools.partial`就是帮助我们创建一个偏函数的，不需要我们自己定义`int2()`，可以直接使用下面的代码创建一个新的函数int2：

```py
>>> import functools
>>> int2 = functools.partial(int, base=2)
>>> int2('1000000')
64
>>> int2('1010101')
85
```

所以，简单总结`functools.partial`的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

注意到上面的新的int2函数，仅仅是把base参数重新设定默认值为2，但也可以在函数调用时传入其他值：

```py
>>> int2('1000000', base=10)
1000000
```

```py
最后，创建偏函数时，实际上可以接收函数对象、*args和**kw这3个参数，当传入：

int2 = functools.partial(int, base=2)
实际上固定了int()函数的关键字参数base，也就是：

int2('10010')
相当于：

kw = { 'base': 2 }
int('10010', **kw)
当传入：

max2 = functools.partial(max, 10)
实际上会把10作为*args的一部分自动加到左边，也就是：

max2(5, 6, 7)
相当于：

args = (10, 5, 6, 7)
max(*args)
结果为10。
```