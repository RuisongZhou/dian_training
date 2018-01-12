# Dian_python学习记录4

## 引用

当你创建了一个对象并将其分配给某个变量时，变量只会查阅（Refer）某个对象，并且它也
不会代表对象本身。也就是说，变量名只是指向你计算机内存中存储了相应对象的那一部
分。这叫作将名称绑定（Binding）给那一个对象。

```py
print('Simple Assignment')
shoplist = ['apple', 'mango', 'carrot', 'banana']
# mylist 只是指向同一对象的另一种名称
mylist = shoplist
# 我购买了第一项项目，所以我将其从列表中删除
del shoplist[0]
print('shoplist is', shoplist)
print('mylist is', mylist)
# 注意到 shoplist 和 mylist 二者都
# 打印出了其中都没有 apple 的同样的列表，以此我们确认
# 它们指向的是同一个对象
print('Copy by making a full slice')
# 通过生成一份完整的切片制作一份列表的副本
mylist = shoplist[:]
# 删除第一个项目
del mylist[0]
print('shoplist is', shoplist)
print('mylist is', mylist)
# 注意到现在两份列表已出现不同
```

输出：

```py
$ python ds_reference.py
Simple Assignment
shoplist is ['mango', 'carrot', 'banana']
mylist is ['mango', 'carrot', 'banana']
Copy by making a full slice
shoplist is ['mango', 'carrot', 'banana']
mylist is ['carrot', 'banana']
```

## 有关字符串的一些内容

你在程序中使用的所有字符串都是`str`类下的对象。下面的案例将演示这种类之下一些有用
的方法。要想获得这些方法的完成清单，你可以查阅`help(str)`。

案例（保存为  ds_str_methods.py  ）：

```py
# 这是一个字符串对象
`name` = 'Swaroop'
if `name`.startswith('Swa'): # 注意是startswith
print('Yes, the string starts with "Swa"')
if 'a' in `name`:
print('Yes, it contains the string "a"')
if `name`.find('war') != -1:
print('Yes, it contains the string "war"')
delimiter = '_*_'
mylist = ['Brazil', 'Russia', 'India', 'China']
print(delimiter.join(mylist))
```

输出：

```py
$ python ds_str_methods.py
Yes, the string starts with "Swa"
Yes, it contains the string "a"
Yes, it contains the string "war"
Brazil_*_Russia_*_India_*_China
```

## 面向对象编程

* 类(class)和对象(object)。
* 从属于对象或类的变量叫做字段(Field)。
* 对象还可以使用属于类的函数来实现某些功能，这种函数叫作类的方法(Method)。
* 字段与方法通称类的属性(Attribute)。
* 通过class可以创建一个类。类方法与普通函数只有一种特定的区别——前者必须有一个额外的名字，这个名字必须添加到参数列表的开头，但是你不用在你调用这个功能时为这个参数赋值，Python 会为它提供。这种特定的变量引用的是对象本身，按照惯例，它被赋予``self``这一名称。

### 类

```py
class Person:
    pass # 一个空的代码块

p = Person()
print(p)

# 输出：
$ python oop_simplestclass.py
<__main__.Person instance at 0x10171f518>
```

类与对象一如函数那般都可以带有方法（Method），唯一的不同在于
我们还拥有一个额外的  `self`  变量。

```py
class Person:
    def say_hi(`self`):
        print('Hello, how are you?')

p = Person()
p.say_hi()
# 前面两行同样可以写作
# Person().say_hi()

输出：

$ python oop_method.py
Hello, how are you?
```

### __init__方法

`__init__` 方法会在类的对象被实例化（Instantiated）时立即运行。这一方法可以对任何你想
进行操作的目标对象进行初始化（Initialization）操作。这里你要注意在 init 前后加上的双下
划线。

```py
class Person:
    def __init__(`self`, `name`):
        `self`.`name` = `name`

def say_hi(`self`):
    print('Hello, my `name` is', `self`.`name`)
p = Person('Swaroop')
p.say_hi()
# 前面两行同时也能写作
# Person('Swaroop').say_hi()

输出：
$ python oop_init.py
Hello, my `name` is Swaroop
```

### 类对象与对象变量

字段（Filed）有两种类型——类变量与对象变量，它们根据究竟是类还是对象拥有这些变量
来进行分类。

类变量（Class Variable）是共享的（Shared）——它们可以被属于该类的所有实例访问。
该类变量只拥有一个副本，当任何一个对象对类变量作出改变时，发生的变动将在其它所有
实例中都会得到体现。

对象变量（Object variable）由类的每一个独立的对象或实例所拥有。在这种情况下，每个对象都拥有属于它自己的字段的副本，也就是说，它们不会被共享，也不会以任何方式与其
它不同实例中的相同名称的字段产生关联。

例如：

```py
class Robot:
"""表示有一个带有名字的机器人。"""
# 一个类变量，用来计数机器人的数量
population = 0

def __init__(self, name):
    """初始化数据"""
    self.name = name
    print("(Initializing {})".format(self.name))

    # 当有人被创建时，机器人
    # 将会增加人口数量
    Robot.population += 1

def die(self):
    """我挂了。"""
    print("{} is being destroyed!".format(self.name))
    Robot.population -= 1
    if Robot.population == 0:
        print("{} was the last one.".format(self.name))
    else:
        print("There are still {:d} robots working.".format(
        Robot.population))

def say_hi(self):
    """来自机器人的诚挚问候
    没问题，你做得到。"""
    print("Greetings, my masters call me {}.".format(self.name))

@classmethod
def how_many(cls):
    """打印出当前的人口数量"""
    print("We have {:d} robots.".format(cls.population))


droid1 = Robot("R2-D2")
droid1.say_hi()
Robot.how_many()

droid2 = Robot("C-3PO")
droid2.say_hi()
Robot.how_many()
print("\nRobots can do some work here.\n")

print("Robots have finished their work. So let's destroy them.")
droid1.die()
droid2.die()

Robot.how_many()
```

输出：

```blank
$ python oop_objvar.py
(Initializing R2-D2)
Greetings, my masters call me R2-D2.
We have 1 robots.
(Initializing C-3PO)
Greetings, my masters call me C-3PO.
We have 2 robots.

Robots can do some work here.

Robots have finished their work. So let's destroy them.
R2-D2 is being destroyed!
There are still 1 robots working.
C-3PO is being destroyed!
C-3PO was the last one.
We have 0 robots.
```

在本例中，`population`属于 `Robot`类，因此它是一个类变量。`name`变量属于一个对象（通过使用 `self`分配），因此它是一个对象变量。

因此，我们通过  Robot.population  而非  `self`.population  引用`population` 类变量。我们对于  `name`  对象变量采用  `self`.`name`  标记法加以称呼，这是这个对象中所具有的方法。记住这个类变量与对象变量之间的简单区别。同时你还要注意当一个对象变量与一个类变量名称相同时，类变量将会被隐藏。

除了  Robot.popluation  ，我们还可以使用  `self.__class__.population`  ，因为每个对象都通过`self.__class__`属性来引用它的类。

`how_many` 实际上是一个属于类而非属于对象的方法。这就意味着我们可以将它定义为一个
`classmethod（类方法）`或是一个`staticmethod(静态方法)`，这取决于我们是否知道我们需不需
要知道我们属于哪个类。由于我们已经引用了一个类变量，因此我们使用`classmethod（类方法）`。

我们使用装饰器（Decorator）将`how_many`方法标记为类方法。

启动`@classmethod`装饰器等于调用：

```py
how_many = classmethod(how_many)
```

## 函数式编程

### 返回函数

例，返回求和函数：

```py
def lazy_sum(*args):
    def sum():
        ax = 0
        for n in args:
            ax = ax + n
        return ax
    return sum
```

当我们调用`lazy_sum()`时，返回的并不是求和结果，而是求和函数：

```py
>>> f = lazy_sum(1, 3, 5, 7, 9)
>>> f
<function lazy_sum.<locals>.sum at 0x101c6ed90>
```

调用函数f时，才真正计算求和的结果：

```py
>>> f()
25
```

* 闭包

注意到返回的函数在其定义内部引用了局部变量`args`，所以，当一个函数返回了一个函数后，其内部的局部变量还被新函数引用，所以，闭包用起来简单，实现起来可不容易。

另一个需要注意的问题是，返回的函数并没有立刻执行，而是直到调用了f()才执行。我们来看一个例子：

```py
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
    return fs

f1, f2, f3 = count()

#在上面的例子中，每次循环，都创建了一个新的函数，然后，把创建的3个函数都返回了。

#你可能认为调用f1()，f2()和f3()结果应该是1，4，9，但实际结果是：

>>> f1()
9
>>> f2()
9
>>> f3()
9
```

如果一定要引用循环变量怎么办？方法是再创建一个函数，用该函数的参数绑定循环变量当前的值，无论该循环变量后续如何更改，已绑定到函数参数的值不变：

```py
def count():
    def f(j):
        def g():
            return j*j
        return g
    fs = []
    for i in range(1, 4):
        fs.append(f(i)) # f(i)立刻被执行，因此i的当前值被传入f()
    return fs


>>> f1, f2, f3 = count()
>>> f1()
1
>>> f2()
4
>>> f3()
9
```

### 匿名函数

关键字`lambda`表示匿名函数，冒号前面的x表示函数参数。

例：

```py
>>> list(map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
[1, 4, 9, 16, 25, 36, 49, 64, 81]

通过对比可以看出，匿名函数lambda x: x * x实际上就是：

def f(x):
    return x * x
```

匿名函数也是一个函数对象，也可以把匿名函数赋值给一个变量，再利用变量来调用该函数：

```py
>>> f = lambda x: x * x
>>> f
<function <lambda> at 0x101c6ef28>
>>> f(5)
25
```

同样，也可以把匿名函数作为返回值返回，比如：

```py
def build(x, y):
    return lambda: x * x + y * y
```

### 装饰器

### 偏函数