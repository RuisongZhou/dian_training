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