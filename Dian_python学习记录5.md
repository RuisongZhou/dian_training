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

### 偏函数