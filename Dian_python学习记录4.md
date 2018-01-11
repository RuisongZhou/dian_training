# Dian_python学习记录4.md

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
name = 'Swaroop'
if name.startswith('Swa'): # 注意是startswith
print('Yes, the string starts with "Swa"')
if 'a' in name:
print('Yes, it contains the string "a"')
if name.find('war') != -1:
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
* 通过class可以创建一个类。类方法与普通函数只有一种特定的区别——前者必须有一个额外的名字，这个名字必须添加到参数列表的开头，但是你不用在你调用这个功能时为这个参数赋值，Python 会为它提供。这种特定的变量引用的是对象本身，按照惯例，它被赋予`self`这一名称。

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
我们还拥有一个额外的  self  变量。

```py
class Person:
    def say_hi(self):
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
    def __init__(self, name):
        self.name = name

def say_hi(self):
    print('Hello, my name is', self.name)
p = Person('Swaroop')
p.say_hi()
# 前面两行同时也能写作
# Person('Swaroop').say_hi()

输出：
$ python oop_init.py
Hello, my name is Swaroop
```

###  类对象与对象变量

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

```
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