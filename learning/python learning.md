# 简介
Python 是一个高层次的结合了解释性、编译性、互动性和面向对象的脚本语言。

# 基础语法
默认情况下，Python3 源码文件以 UTF-8 编码，所有字符串都是 unicode 字符串。
## 标识符
第一个字符必须以字母（a-z, A-Z）或下划线 `_` 。其他的部分由字母、数字和下划线组成。**大小写敏感**，count 和 Count 是不同的标识符。

## 保留关键字
保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：
```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def',
 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal',
 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

| 类别       | 关键字   | 说明                                      |
|------------|----------|-------------------------------------------|
| 逻辑值     | True     | 布尔真值                                  |
|            | False    | 布尔假值                                  |
|            | None     | 表示空值或无值                            |
| 逻辑运算    | and      | 逻辑与运算                                |
|            | or       | 逻辑或运算                                |
|            | not      | 逻辑非运算                                |
| 条件控制    | if       | 条件判断语句                              |
|            | elif     | 否则如果（else if 的缩写）                |
|            | else     | 否则分支                                  |
| 循环控制    | for      | 迭代循环                                  |
|            | while    | 条件循环                                  |
|            | break    | 跳出循环                                  |
|            | continue | 跳过当前循环的剩余部分，进入下一次迭代      |
| 异常处理    | try      | 尝试执行代码块                            |
|            | except   | 捕获异常                                  |
|            | finally  | 无论是否发生异常都会执行的代码块          |
|            | raise    | 抛出异常                                  |
| 函数定义    | def      | 定义函数                                  |
|            | return   | 从函数返回值                              |
|            | lambda   | 创建匿名函数                              |
| 类与对象    | class    | 定义类                                    |
|            | del      | 删除对象引用                              |
| 模块导入    | import   | 导入模块                                  |
|            | from     | 从模块导入特定部分                        |
|            | as       | 为导入的模块或对象创建别名                |
| 作用域      | global   | 声明全局变量                              |
|            | nonlocal | 声明非局部变量（用于嵌套函数）            |
| 异步编程    | async    | 声明异步函数                              |
|            | await    | 等待异步操作完成                          |
| 其他        | assert   | 断言，用于测试条件是否为真                |
|            | in       | 检查成员关系                              |
|            | is       | 检查对象身份（是否是同一个对象）            |
|            | pass     | 空语句，用于占位                          |
|            | with     | 上下文管理器，用于资源管理                  |
|            | yield    | 从生成器函数返回值                         |

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 \ 来实现多行语句，例如：
```python
total = item_one + \
        item_two + \
        item_three
```
在 [], {}, 或 () 中的多行语句，不需要使用反斜杠 \，例如：
```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

## print 输出
print 默认输出是换行的，如果要实现不换行需要在变量末尾加上 `end=""`：
`print( x, end=" " )`

## import 与 from...import
在 python 用 import 或者 from...import 来导入相应的模块。

将整个模块(somemodule)导入，格式为： `import somemodule` 。
- 使用时需通过模块名访问模块中的对象
- 不会与当前命名空间中的其他对象冲突
- 代码中明确知道哪些对象来自哪个模块，因为总是使用模块名前缀
- 适用于需要使用模块中多个对象的情况
```python
import math

result = math.sqrt(16)
print(result)  # 输出 4.0
```

从某个模块中导入某个函数,格式为： `from somemodule import somefunction` 。
- 使用时直接引用导入的对象，不需模块名前缀
- 可能会与当前命名空间中的其他对象发生命名冲突
- 代码中直接使用对象名，可能难以看出这些对象来自哪个模块
- 适用于只需要使用模块中少量对象的情况，节省内存
```python
from math import sqrt

result = sqrt(16)
print(result)  # 输出 4.0
```
```python
from math import sqrt
from cmath import sqrt  # 复数的 sqrt

result = sqrt(-1)  # 可能会混淆使用的 sqrt 函数
print(result)
```

从某个模块中导入多个函数,格式为： `from somemodule import firstfunc, secondfunc, thirdfunc`

将某个模块中的全部函数导入，格式为： `from somemodule import *`
- 导入模块中的所有对象到当前命名空间
- 可能导致命名冲突，降低代码可读性，不推荐使用

# 基本数据类型
Python 中的变量**不需要声明**。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。

在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。

Python允许你同时为多个变量赋值。例如：`a = b = c = 1`

也可以为多个对象指定多个变量。例如：`a, b, c = 1, 2, "runoob"`

可以通过 type() 函数查看变量的类型：`print(type(x))`

## 标准数据类型
常见的数据类型有：
- Number（数字）
- String（字符串）
- bool（布尔类型）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

Python3 的六个标准数据类型中：

- 不可变数据（3 个）：Number（数字）、String（字符串）、Tuple（元组）；
- 可变数据（3 个）：List（列表）、Dictionary（字典）、Set（集合）。

此外还有一些高级的数据类型，如: 字节数组类型(bytes)。

### Number（数字）
四种类型：整数、布尔型、浮点数和复数。
- int (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- bool (布尔), 如 True。
- float (浮点数), 如 1.23、3E-2
- complex (复数) - 复数由实部和虚部组成，形式为 `a + bj` 或者 `complex(a,b)`，其中 a 是实部，b 是虚部，j 表示虚数单位。如 1 + 2j、 1.1 + 2.2j ， 复数的实部 a 和虚部 b 都是浮点型。

可以用 isinstance 来判断类型：
```python
>>> a = 111
>>> isinstance(a, int)
True
>>>
```

isinstance 和 type 的区别在于：
- type 只检查对象的精确类型。
- isinstance 会检查对象是否是某个类或其子类的实例，因此它在继承链中更加灵活。

```python
>>> class A:
...     pass
... 
>>> class B(A):
...     pass
... 
>>> isinstance(A(), A)
True
>>> type(A()) == A 
True
>>> isinstance(B(), A)
True
>>> type(B()) == A
False
```

Python3 中，bool 是 int 的子类，True 和 False 可以和数字相加， `True==1`、`False==0` 会返回 True。

可以通过使用 del 语句删除单个或多个对象。例如：
```python
del var
del var_a, var_b
```

#### 数值运算
```python
>>> 5 + 4  # 加法
9
>>> 4.3 - 2 # 减法
2.3
>>> 3 * 7  # 乘法
21
>>> 2 / 4  # 除法，得到一个浮点数
0.5
>>> 2 // 4 # 除法，得到一个整数
0
>>> 17 % 3 # 取余 
2
>>> 2 ** 5 # 乘方
32
```

### 字符串(String)
- Python 中单引号 `'` 和双引号 `"` 使用完全相同。
- 使用三引号(`'''` 或 `"""`)可以指定一个多行字符串。
- 转义符 `\`。
- 反斜杠可以用来转义，使用 **r** 可以让反斜杠不发生转义。 如 `r"this is a line with \n"` 则 `\n` 会显示，并不是换行。
- 字符串可以用 `+` 运算符连接在一起，用 `*` 运算符重复。
- Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。
- Python 中的**字符串不能改变**。向一个索引位置赋值，比如 `word[0] = 'm'` 会导致错误。
- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。
- 字符串切片 `str[start:end]`，其中 start（包含）是切片开始的索引，end（不包含）是切片结束的索引。
- 字符串的切片可以加上步长参数 step，语法格式如下：`str[start:end:step]`

```python
word = '字符串'
sentence = "这是一个句子。"
paragraph = """这是一个段落，
可以由多行组成"""
```

### bool（布尔类型）
在 Python 中，所有非零的数字和非空的字符串、列表、元组等数据类型都被视为 True，只有 0、空字符串、空列表、空元组等被视为 False。因此，在进行布尔类型转换时，需要注意数据类型的真假性。

### List（列表）
列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）。

**列表是写在方括号 [] 之间、用逗号分隔开的元素列表。**

和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。索引值以 0 为开始值，-1 为从末尾的开始位置。

<img width="1366" height="720" alt="image" src="https://github.com/user-attachments/assets/7e9a011e-3e90-4ac3-aab9-1f8687eaeea3" />

加号 + 是列表连接运算符，星号 * 是重复操作。如下实例：
```python
#!/usr/bin/python3

list = [ 'abcd', 786 , 2.23, 'runoob', 70.2 ]  # 定义一个列表
tinylist = [123, 'runoob']

print (list)            # 打印整个列表
print (list[:]) 
print (list[-2:]) 
print (list[0])         # 打印列表的第一个元素
print (list[1:3])       # 打印列表第二到第四个元素（不包含第四个元素）
print (list[2:])        # 打印列表从第三个元素开始到末尾
print (tinylist * 2)    # 打印tinylist列表两次
print (list + tinylist)  # 打印两个列表拼接在一起的结果
```
输出结果：
```python
['abcd', 786, 2.23, 'runoob', 70.2]
['abcd', 786, 2.23, 'runoob', 70.2]
['runoob', 70.2]
abcd
[786, 2.23]
[2.23, 'runoob', 70.2]
[123, 'runoob', 123, 'runoob']
['abcd', 786, 2.23, 'runoob', 70.2, 123, 'runoob']
```
```python
>>> a = [1, 2, 3, 4, 5, 6]
>>> a[0] = 9
>>> a[2:5] = [13, 14, 15]
>>> a
[9, 2, 13, 14, 15, 6]
>>> a[2:5] = []   # 将对应的元素值设置为 [] 
>>> a
[9, 2, 6]
```
Python 列表截取可以接收第三个参数，参数作用是截取的步长，以下实例在索引 1 到索引 4 的位置并设置为步长为 2（间隔一个位置）来截取字符串：
<img width="711" height="318" alt="image" src="https://github.com/user-attachments/assets/89d53865-429a-4a2c-96d3-af41a9787f60" />

翻转字符串可以理解为：逆向遍历列表，并且以步长为 1 的方式 每隔一个元素取一个。
```python
def reverseWords(input):
     
    # 通过空格将字符串分隔符，把各个单词分隔为列表
    inputWords = input.split(" ")
 
    # 翻转字符串
    inputWords=inputWords[-1::-1]
 
    # 重新组合字符串
    output = ' '.join(inputWords)
     
    return output
```

### Tuple（元组）
元组（tuple）与列表类似，不同之处在于**元组的元素不能修改**。**元组写在小括号 () 里，元素之间用逗号隔开。**

元组中的元素类型也可以不相同：
```python
#!/usr/bin/python3

tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2  )
tinytuple = (123, 'runoob')

print (tuple)             # 输出完整元组
print (tuple[0])          # 输出元组的第一个元素
print (tuple[1:3])        # 输出从第二个元素开始到第三个元素
print (tuple[2:])         # 输出从第三个元素开始的所有元素
print (tinytuple * 2)     # 输出两次元组
print (tuple + tinytuple) # 连接元组
```

输出结果：
```python
('abcd', 786, 2.23, 'runoob', 70.2)
abcd
(786, 2.23)
(2.23, 'runoob', 70.2)
(123, 'runoob', 123, 'runoob')
('abcd', 786, 2.23, 'runoob', 70.2, 123, 'runoob')

```

其实，可以把字符串看作一种特殊的元组。
```python
>>> tup = (1, 2, 3, 4, 5, 6)
>>> print(tup[0])
1
>>> print(tup[1:5])
(2, 3, 4, 5)
>>> tup[0] = 11  # 修改元组元素的操作是非法的
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>>
```
虽然tuple的元素不可改变，但它可以包含可变的对象，比如list列表。

构造包含 0 个或 1 个元素的元组比较特殊，所以有一些额外的语法规则：
```python
tup1 = ()    # 空元组
tup2 = (20,) # 一个元素，需要在元素后添加逗号

```
如果你想创建只有一个元素的元组，需要注意在元素后面添加一个逗号，以区分它是一个元组而不是一个普通的值，这是因为在没有逗号的情况下，Python会将括号解释为数学运算中的括号，而不是元组的表示。

string、list 和 tuple 都属于 sequence（序列）。

### Set（集合）
集合（Set）是一种**无序、可变**的数据类型，用于存储唯一的元素。集合中的元素**不会重复**，并且可以进行交集、并集、差集等常见的集合操作。**集合使用大括号 {} 表示，元素之间用逗号 , 分隔。**

可以使用 set() 函数创建集合。创建一个空集合必须用 `set()` 而不是 `{ }`，因为 `{ }` 是用来创建一个空字典。
```python
parame = {value01,value02,...}
或者
set(value)
```
```python
#!/usr/bin/python3

sites = {'Google', 'Taobao', 'Runoob', 'Facebook', 'Zhihu', 'Baidu'}

print(sites)   # 输出集合，重复的元素被自动去掉

# 成员测试
if 'Runoob' in sites :
    print('Runoob 在集合中')
else :
    print('Runoob 不在集合中')


# set可以进行集合运算
a = set('abracadabra')
b = set('alacazam')

print(a)

print(a - b)     # a 和 b 的差集

print(a | b)     # a 和 b 的并集

print(a & b)     # a 和 b 的交集

print(a ^ b)     # a 和 b 中不同时存在的元素
```
输出结果：
```python
{'Zhihu', 'Baidu', 'Taobao', 'Runoob', 'Google', 'Facebook'}
Runoob 在集合中
{'b', 'c', 'a', 'r', 'd'}
{'r', 'b', 'd'}
{'b', 'c', 'a', 'z', 'm', 'r', 'l', 'd'}
{'c', 'a'}
{'z', 'b', 'm', 'r', 'l', 'd'}

```
### Dictionary（字典）
列表是**有序**的对象集合，字典是**无序**的对象集合。两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。

字典是一种映射类型，字典用 `{ }` 标识，它是一个无序的 **键(key) : 值(value)** 的集合。

键(key)必须使用不可变类型。在同一个字典中，键(key)必须是唯一的。
```python
#!/usr/bin/python3

dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]     = "2 - 菜鸟工具"

tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}

print (dict)
print (dict['one'])       # 输出键为 'one' 的值
print (dict[2])           # 输出键为 2 的值
print (tinydict)          # 输出完整的字典
print (tinydict.keys())   # 输出所有键
print (tinydict.values()) # 输出所有值
```
输出结果：
```python
{'one': '1 - 菜鸟教程', 2: '2 - 菜鸟工具'}
1 - 菜鸟教程
2 - 菜鸟工具
{'name': 'runoob', 'code': 1, 'site': 'www.runoob.com'}
dict_keys(['name', 'code', 'site'])
dict_values(['runoob', 1, 'www.runoob.com'])
```
构造函数 dict() 可以直接从键值对序列中构建字典，
```python
>>> dict([('Runoob', 1), ('Google', 2), ('Taobao', 3)])
{'Runoob': 1, 'Google': 2, 'Taobao': 3}
>>> {x: x**2 for x in (2, 4, 6)} // 这是字典推导式，语法形如：{key_expr: value_expr for 变量 in 可迭代对象 [if 条件]}。
{2: 4, 4: 16, 6: 36}
>>> dict(Runoob=1, Google=2, Taobao=3)
{'Runoob': 1, 'Google': 2, 'Taobao': 3}
```

注意：

1、字典是一种映射类型，它的元素是键值对。

2、字典的关键字必须为不可变类型，且不能重复。

3、创建空字典使用 { }。

### bytes 类型
bytes 类型表示的是不可变的二进制序列（byte sequence）。与字符串类型不同的是，bytes 类型中的元素是整数值（0 到 255 之间的整数），而不是 Unicode 字符。

创建 bytes 对象的方式有多种，最常见的方式是使用 b 前缀：

此外，也可以使用 bytes() 函数将其他类型的对象转换为 bytes 类型。bytes() 函数的第一个参数是要转换的对象，第二个参数是编码方式，如果省略第二个参数，则默认使用 UTF-8 编码：
```python
x = bytes("hello", encoding="utf-8")
```

与字符串类型类似，bytes 类型也支持许多操作和方法，如切片、拼接、查找、替换等等。同时，由于 bytes 类型是不可变的，因此在进行修改操作时需要创建一个新的 bytes 对象。
```python
x = b"hello"
y = x[1:3]  # 切片操作，得到 b"el"
z = x + b"world"  # 拼接操作，得到 b"helloworld"
if x[0] == ord("h"):
    print("The first element is 'h'")
```
bytes 类型中的元素是整数值，因此在进行比较操作时需要使用相应的整数值。其中 ord() 函数用于将字符转换为相应的整数值。

## 数据类型转换

| 函数                | 描述                                      |
| ------------------- | ----------------------------------------- |
| int(x [,base])      | 将x转换为一个整数                          |
| float(x)            | 将x转换到一个浮点数                        |
| complex(real [,imag]) | 创建一个复数                              |
| str(x)              | 将对象 x 转换为字符串                      |
| repr(x)             | 将对象 x 转换为表达式字符串                |
| eval(str)           | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
| tuple(s)            | 将序列 s 转换为一个元组                    |
| list(s)             | 将序列 s 转换为一个列表                    |
| set(s)              | 转换为可变集合                            |
| dict(d)             | 创建一个字典。d 必须是一个 (key, value)元组序列。 |
| frozenset(s)        | 转换为不可变集合                          |
| chr(x)              | 将一个整数转换为一个字符                  |
| ord(x)              | 将一个字符转换为它的整数值                |
| hex(x)              | 将一个整数转换为一个十六进制字符串        |
| oct(x)              | 将一个整数转换为一个八进制字符串          |

