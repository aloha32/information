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
在整数除法中，除法 `/` 总是返回一个浮点数，如果只想得到整数的结果，丢弃可能的分数部分，可以使用运算符 `//`

> `//` 得到的并不一定是整数类型的数，它与分母分子的数据类型有关系。
```python
>>> 7//2
3
>>> 7.0//2
3.0
>>> 7//2.0
3.0
>>> 
```

#### 数学函数

| 函数           | 返回值（描述）                                               |
| -------------- | ------------------------------------------------------------ |
| abs(x)         | 返回数字的绝对值，如abs(-10) 返回 10                         |
| ceil(x)        | 返回数字的上入整数，如math.ceil(4.1) 返回 5                  |
| cmp(x, y)      | 如果 x < y 返回 -1, 如果 x == y 返回 0, 如果 x > y 返回 1。**Python 3 已废弃，使用 (x>y)-(x<y) 替换。**|
| exp(x)         | 返回e的x次幂(e^x),如math.exp(1) 返回2.718281828459045        |
| fabs(x)        | 以浮点数形式返回数字的绝对值，如math.fabs(-10)返回10.0       |
| floor(x)       | 返回数字的下舍整数，如math.floor(4.9)返回 4                  |
| log(x)         | 如math.log(math.e)返回1.0,math.log(100,10)返回2.0            |
| log10(x)       | 返回以10为基数的x的对数，如math.log10(100)返回 2.0           |
| max(x1, x2,...) | 返回给定参数的最大值，参数可以为序列。                       |
| min(x1, x2,...) | 返回给定参数的最小值，参数可以为序列。                       |
| modf(x)        | 返回x的整数部分与小数部分，两部分的数值符号与x相同，整数部分以浮点型表示。 |
| pow(x, y)      | x**y 运算后的值。                                             |
| round(x [,n])  | 返回浮点数 x 的四舍五入值，如给出 n 值，则代表舍入到小数点后的位数。<br>其实准确的说是保留值将保留到离上一位更近的一端。 |
| sqrt(x)        | 返回数字x的平方根。                                           |

#### 随机数函数


| 函数               | 描述                                                                 |
|--------------------|----------------------------------------------------------------------|
| choice(seq)        | 从序列的元素中随机挑选一个元素，比如`random.choice(range(10))`，从0到9中随机挑选一个整数。 |
| randrange([start,] stop [,step]) | 从指定范围内，按指定基数递增的集合中获取一个随机数，基数默认值为 1 |
| random()           | 随机生成下一个实数，它在[0,1)范围内。                                   |
| seed([x])          | 改变随机数生成器的种子seed。如果你不了解其原理，你不必特别去设定seed，Python会帮你选择seed。 |
| shuffle(lst)       | 将序列的所有元素随机排序                                               |
| uniform(x, y)      | 随机生成下一个实数，它在[x,y]范围内。                                   |

#### 三角函数

| 函数           | 描述                                       |
|----------------|--------------------------------------------|
| acos(x)        | 返回x的反余弦弧度值。                      |
| asin(x)        | 返回x的反正弦弧度值。                      |
| atan(x)        | 返回x的反正切弧度值。                      |
| atan2(y, x)    | 返回给定的 X 及 Y 坐标值的反正切值。       |
| cos(x)         | 返回x的弧度的余弦值。                      |
| hypot(x, y)    | 返回欧几里德范数 sqrt(x*x + y*y)。         |
| sin(x)         | 返回的x弧度的正弦值。                      |
| tan(x)         | 返回x弧度的正切值。                        |
| degrees(x)     | 将弧度转换为角度，如`degrees(math.pi/2)`，返回90.0 |
| radians(x)     | 将角度转换为弧度                           |

#### 数学常量

| 常量 | 描述 |
|------|------|
| pi   | 数学常量 pi（圆周率，一般以π来表示） |
| e    | 数学常量 e，e即自然常数（自然常数）。 |


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

#### 字符串格式化
在 Python 中，字符串格式化使用与 C 中 sprintf 函数一样的语法。
```python
#!/usr/bin/python3
 
print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
```

| 符号 | 描述 |
|------|------|
| %c   | 格式化字符及其ASCII码 |
| %s   | 格式化字符串 |
| %d   | 格式化整数 |
| %u   | 格式化无符号整型 |
| %o   | 格式化无符号八进制数 |
| %x   | 格式化无符号十六进制数 |
| %X   | 格式化无符号十六进制数（大写） |
| %f   | 格式化浮点数字，可指定小数点后的精度 |
| %e   | 用科学计数法格式化浮点数 |
| %E   | 作用同%e，用科学计数法格式化浮点数 |
| %g   | %f和%e的简写 |
| %G   | %f 和 %E 的简写 |
| %p   | 用十六进制数格式化变量的地址 |

#### f-string
f-string 是 python3.6 之后版本添加的，称之为字面量格式化字符串，是新的格式化字符串的语法。

之前我们习惯用百分号 (%):
```python
>>> name = 'Runoob'
>>> 'Hello %s' % name
'Hello Runoob'
```
f-string 格式化字符串以 f 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去，实例如下：
```python
>>> name = 'Runoob'
>>> f'Hello {name}'  # 替换变量
'Hello Runoob'
>>> f'{1+2}'         # 使用表达式
'3'

>>> w = {'name': 'Runoob', 'url': 'www.runoob.com'}
>>> f'{w["name"]}: {w["url"]}'
'Runoob: www.runoob.com'
```
在 Python 3.8 的版本中可以使用 = 符号来拼接运算表达式与结果：
```python
>>> x = 1
>>> print(f'{x+1}')   # Python 3.6
2

>>> x = 1
>>> print(f'{x+1=}')   # Python 3.8
x+1=2
```

#### Unicode 字符串
在Python3中，所有的字符串都是Unicode字符串。

#### 字符串内建函数

| 方法 | 描述 |
|------|------|
| `capitalize()` | 将字符串的第一个字符转换为大写 |
| `center(width, fillchar)` | 返回一个指定的宽度 width 居中的字符串，fillchar 为填充的字符，默认为空格。 |
| `count(str, beg=0, end=len(string))` | 返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数 |
| `bytes.decode(encoding="utf-8", errors="strict")` | Python3 中没有 decode 方法，但我们可以使用 bytes 对象的 decode() 方法来解码给定的 bytes 对象，这个 bytes 对象可以由 str.encode() 来编码返回。 |
| `encode(encoding='UTF-8', errors='strict')` | 以 encoding 指定的编码格式编码字符串，如果出错默认报一个 ValueError 的异常，除非 errors 指定的是 'ignore' 或者 'replace' |
| `endswith(suffix, beg=0, end=len(string))` | 检查字符串是否以 suffix 结束，如果 beg 或者 end 指定则检查指定的范围内是否以 suffix 结束，如果是，返回 True，否则返回 False。 |
| `expandtabs(tabsize=8)` | 把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8 。 |
| `find(str, beg=0, end=len(string))` | 检测 str 是否包含在字符串中，如果指定范围 beg 和 end ，则检查是否包含在指定范围内，如果包含返回开始的索引值，否则返回-1 |
| `index(str, beg=0, end=len(string))` | 跟 find()方法一样，只不过如果 str 不在字符串中会报一个异常。 |
| `isalnum()` | 检查字符串是否由字母和数字组成，即字符串中的所有字符都是字母或数字。如果字符串至少有一个字符，并且所有字符都是字母或数字，则返回 True；否则返回 False。 |
| `isalpha()` | 如果字符串至少有一个字符并且所有字符都是字母或中文文字则返回 True，否则返回 False |
| `isdigit()` | 如果字符串只包含数字则返回 True 否则返回 False。 |
| `islower()` | 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False |
| `isnumeric()` | 如果字符串中只包含数字字符，则返回 True，否则返回 False |
| `isspace()` | 如果字符串中只包含空白，则返回 True，否则返回 False。 |
| `istitle()` | 如果字符串是标题化的(见 title())则返回 True，否则返回 False |
| `isupper()` | 如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False |
| `join(seq)` | 以指定字符串作为分隔符，将 seq 中所有的元素(的字符串表示)合并为一个新的字符串 |
| `len(string)` | 返回字符串长度 |
| `ljust(width[, fillchar])` | 返回一个原字符串左对齐，并使用 fillchar 填充至长度 width 的新字符串，fillchar 默认为空格。 |
| `lower()` | 转换字符串中所有大写字符为小写。 |
| `lstrip()` | 截掉字符串左边的空格或指定字符。 |
| `maketrans()` | 创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。 |
| `max(str)` | 返回字符串 str 中最大的字母。 |
| `min(str)` | 返回字符串 str 中最小的字母。 |
| `replace(old, new [, max])` | 把 将字符串中的 old 替换成 new，如果 max 指定，则替换不超过 max 次。 |
| `rfind(str, beg=0,end=len(string))` | 类似于 find()函数，不过是从右边开始查找。 |
| `rindex(str, beg=0, end=len(string))` | 类似于 index()，不过是从右边开始。 |
| `rjust(width[, fillchar])` | 返回一个原字符串右对齐，并使用fillchar(默认空格) 填充至长度 width 的新字符串 |
| `rstrip()` | 删除字符串末尾的空格或指定字符。 |
| `split(str="", num=string.count(str))` | 以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串 |
| `splitlines([keepends])` | 按照行('\r', '\r\n', '\n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。 |
| `startswith(substr, beg=0,end=len(string))` | 检查字符串是否是以指定子字符串 substr 开头，是则返回 True，否则返回 False。如果 beg 和 end 指定值，则在指定范围内检查。 |
| `strip([chars])` | 在字符串上执行 lstrip()和 rstrip() |
| `swapcase()` | 将字符串中大写转换为小写，小写转换为大写 |
| `title()` | 返回"标题化"的字符串，就是说所有单词都是以大写开始，其余字母均为小写(见 istitle()) |
| `translate(table, deletechars="")` | 根据 table 给出的表(包含 256 个字符)转换 string 的字符，要过滤掉的字符放到 deletechars 参数中 |
| `upper()` | 转换字符串中的小写字母为大写 |
| `zfill(width)` | 返回长度为 width 的字符串，原字符串右对齐，前面填充0 |
| `isdecimal()` | 检查字符串是否只包含十进制字符，如果是返回 true，否则返回 false。 |

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

#### 更新列表
可以对列表的数据项进行修改或更新，也可以使用 `append()` 方法来添加列表项

可以使用 del 语句来删除列表中的元素

#### 列表比较
列表比较需要引入 operator 模块的 eq 方法
```python
# 导入 operator 模块
import operator

a = [1, 2]
b = [2, 3]
c = [2, 3]
print("operator.eq(a,b): ", operator.eq(a,b))
print("operator.eq(c,b): ", operator.eq(c,b))
```
输出结果为：
```python
operator.eq(a,b):  False
operator.eq(c,b):  True
```
更多operator模块详见：[菜鸟教程](https://www.runoob.com/python3/python-operator.html)

#### 列表函数&方法
函数:

| 函数 | 描述 |
|------|------|
| `len(list)` | 列表元素个数 |
| `max(list)` | 返回列表元素最大值 |
| `min(list)` | 返回列表元素最小值 |
| `list(seq)` | 将元组转换为列表 |

方法:

| 方法 | 描述 |
|------|------|
| `list.append(obj)` | 在列表末尾添加新的对象 |
| `list.count(obj)` | 统计某个元素在列表中出现的次数 |
| `list.extend(seq)` | 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表） |
| `list.index(obj)` | 从列表中找出某个值第一个匹配项的索引位置 |
| `list.insert(index, obj)` | 将对象插入列表 |
| `list.pop([index=-1])` | 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值 |
| `list.remove(obj)` | 移除列表中某个值的第一个匹配项 |
| `list.reverse()` | 反向列表中元素 |
| `list.sort(key=None, reverse=False)` | 对原列表进行排序 |
| `list.clear()` | 清空列表 |
| `list.copy()` | 复制列表 |

```python
>>> a = [66.25, 333, 333, 1, 1234.5]
>>> print(a.count(333), a.count(66.25), a.count('x'))
2 1 0
>>> a.insert(2, -1)
>>> a.append(333)
>>> a
[66.25, 333, -1, 333, 1, 1234.5, 333]
>>> a.index(333)
1
>>> a.remove(333)
>>> a
[66.25, -1, 333, 1, 1234.5, 333]
>>> a.reverse()
>>> a
[333, 1234.5, 1, 333, -1, 66.25]
>>> a.sort()
>>> a
[-1, 1, 66.25, 333, 333, 1234.5]
```
注意：类似 insert, remove 或 sort 等修改列表的方法没有返回值。

#### 将列表当做栈使用
在 Python 中，可以使用列表（list）来实现栈的功能。列表提供了一些方法，使其非常适合用于栈操作，特别是 `append()` 和 `pop()` 方法。

栈操作
- 压入（Push）: 将一个元素添加到栈的顶端。
- 弹出（Pop）: 移除并返回栈顶元素。
- 查看栈顶元素（Peek/Top）: 返回栈顶元素而不移除它。
- 检查是否为空（IsEmpty）: 检查栈是否为空。
- 获取栈的大小（Size）: 获取栈中元素的数量。

1. 创建空栈
```python
stack = []
```

2. push
```python
stack.append(1)
stack.append(2)
stack.append(3)
print(stack)  # 输出: [1, 2, 3]
```

3. pop
```python
top_element = stack.pop()
print(top_element)  # 输出: 3
print(stack)        # 输出: [1, 2]
```

4. top
```python
top_element = stack[-1]
print(top_element)  # 输出: 2
```

5. isempty
```python
is_empty = len(stack) == 0
print(is_empty)  # 输出: False
```

6. size
```python
size = len(stack)
print(size)  # 输出: 2
```

完整实例：
```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
        else:
            raise IndexError("pop from empty stack")

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
        else:
            raise IndexError("peek from empty stack")

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)

# 使用示例
stack = Stack()
stack.push(1)
stack.push(2)
stack.push(3)

print("栈顶元素:", stack.peek())  # 输出: 栈顶元素: 3
print("栈大小:", stack.size())    # 输出: 栈大小: 3

print("弹出元素:", stack.pop())  # 输出: 弹出元素: 3
print("栈是否为空:", stack.is_empty())  # 输出: 栈是否为空: False
print("栈大小:", stack.size())    # 输出: 栈大小: 2
```

#### 将列表当作队列使用
在 Python 中，列表（list）可以用作队列（queue），但由于列表的特点，直接使用列表来实现队列并不是最优的选择。

使用列表时，如果频繁地在列表的开头插入或删除元素，性能会受到影响，因为这些操作的时间复杂度是 `O(n)`。为了解决这个问题，Python 提供了 `collections.deque`，它是双端队列，可以在两端高效地添加和删除元素。

使用 deque 实现队列的示例：

```python
from collections import deque

# 创建一个空队列
queue = deque()

# 向队尾添加元素
queue.append('a')
queue.append('b')
queue.append('c')

print("队列状态:", queue)  # 输出: 队列状态: deque(['a', 'b', 'c'])

# 从队首移除元素
first_element = queue.popleft()
print("移除的元素:", first_element)  # 输出: 移除的元素: a
print("队列状态:", queue)            # 输出: 队列状态: deque(['b', 'c'])

# 查看队首元素（不移除）
front_element = queue[0]
print("队首元素:", front_element)    # 输出: 队首元素: b

# 检查队列是否为空
is_empty = len(queue) == 0
print("队列是否为空:", is_empty)     # 输出: 队列是否为空: False

# 获取队列大小
size = len(queue)
print("队列大小:", size)            # 输出: 队列大小: 2
```

使用 pop(0) 方法从队首移除元素：
```python
first_element = queue.pop(0)
print("移除的元素:", first_element)  # 输出: 移除的元素: a
print("队列状态:", queue)            # 输出: 队列状态: ['b', 'c']
```

实例（使用列表实现队列）:
```python
class Queue:
    def __init__(self):
        self.queue = []

    def enqueue(self, item):
        self.queue.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.queue.pop(0)
        else:
            raise IndexError("dequeue from empty queue")

    def peek(self):
        if not self.is_empty():
            return self.queue[0]
        else:
            raise IndexError("peek from empty queue")

    def is_empty(self):
        return len(self.queue) == 0

    def size(self):
        return len(self.queue)

# 使用示例
queue = Queue()
queue.enqueue('a')
queue.enqueue('b')
queue.enqueue('c')

print("队首元素:", queue.peek())    # 输出: 队首元素: a
print("队列大小:", queue.size())    # 输出: 队列大小: 3

print("移除的元素:", queue.dequeue())  # 输出: 移除的元素: a
print("队列是否为空:", queue.is_empty())  # 输出: 队列是否为空: False
print("队列大小:", queue.size())    # 输出: 队列大小: 2
```

**del 语句**:使用 del 语句可以从一个列表中根据索引来删除一个元素，而不是值来删除元素。
```python
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> del a[:]
>>> a
[]
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

其实，可以把字符串看作一种特殊的元组。元组中的元素值是不允许修改的，但我们可以对元组进行连接组合
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

#### 删除元组
元组中的元素值是不允许删除的，但可以使用del语句来删除**整个元组**

#### 关于元组是不可变的
所谓元组的不可变指的是元组所指向的内存中的内容不可变。
```python
>>> tup = ('r', 'u', 'n', 'o', 'o', 'b')
>>> tup[0] = 'g'     # 不支持修改元素
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> id(tup)     # 查看内存地址
4440687904
>>> tup = (1,2,3)
>>> id(tup)
4441088800    # 内存地址不一样了
```
从以上实例可以看出，重新赋值的元组 tup，绑定到新的对象了，不是修改了原来的对象。

元组在输出时总是有括号的，以便于正确表达嵌套结构。在输入时可能有或没有括号， 不过括号通常是必须的（如果元组是更大的表达式的一部分）。
```python
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```


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

#### 集合的基本操作
##### 添加元素
`s.add( x )`将元素 x 添加到集合 s 中，如果元素已存在，则不进行任何操作。
```python
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.add("Facebook")
>>> print(thisset)
{'Taobao', 'Facebook', 'Google', 'Runoob'}
```

还有一个方法，也可以添加元素，且参数可以是列表，元组，字典等，语法格式如下：`s.update( x )` ，x 可以有多个，用逗号分开。
```python
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.update({1,3})
>>> print(thisset)
{1, 3, 'Google', 'Taobao', 'Runoob'}
>>> thisset.update([1,4],[5,6])  
>>> print(thisset)
{1, 3, 4, 5, 6, 'Google', 'Taobao', 'Runoob'}
>>>
```

##### 移除元素
`s.remove( x )`将元素 x 从集合 s 中移除，如果元素不存在，则会发生错误。

还有一个方法也是移除集合中的元素，且如果元素不存在，不会发生错误。格式如下所示：`s.discard( x )`
```python
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.discard("Facebook")  # 不存在不会发生错误
>>> print(thisset)
{'Taobao', 'Google', 'Runoob'}
```

也可以设置**随机删除**集合中的一个元素，语法格式如下：`s.pop() ` ，set 集合的 pop 方法会对集合进行无序的排列，然后将这个无序排列集合的左面第一个元素进行删除。

##### 计算集合元素个数
`len(s)`计算集合 s 元素个数。

##### 清空集合
`s.clear()`清空集合 s。
```python
>>> thisset = set(("Google", "Runoob", "Taobao"))
>>> thisset.clear()
>>> print(thisset)
set()
```

##### 判断元素是否在集合中存在
`x in s`判断元素 x 是否在集合 s 中，存在返回 True，不存在返回 False。

<img width="1025" height="1020" alt="image" src="https://github.com/user-attachments/assets/1a684292-43f5-4b3c-9261-283cda6faf56" />


```python
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # 删除重复的
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # 检测成员
True
>>> 'crabgrass' in basket
False

>>> # 以下演示了两个集合的操作
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # a 中唯一的字母
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # 在 a 中的字母，但不在 b 中
{'r', 'd', 'b'}
>>> a | b                              # 在 a 或 b 中的字母
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # 在 a 和 b 中都有的字母
{'a', 'c'}
>>> a ^ b                              # 在 a 或 b 中的字母，但不同时在 a 和 b 中
{'r', 'd', 'b', 'm', 'z', 'l'}
```
集合也支持推导式：
```python
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}
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

#### 删除字典元素
能删单一的元素也能清空字典，清空只需一项操作。

显式删除一个字典用del命令，如下实例：
```python
#!/usr/bin/python3
 
tinydict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
 
del tinydict['Name'] # 删除键 'Name'
tinydict.clear()     # 清空字典
del tinydict         # 删除字典
```

#### 字典键的特性
字典值可以是任何的 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。

1）不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住

2）键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行

#### 内置函数&方法
<img width="1014" height="501" alt="image" src="https://github.com/user-attachments/assets/34c1a707-36fc-40dc-8fb0-ab9b29633a56" />


| 方法 | 描述 |
|------|------|
| `dict.clear()` | 删除字典内所有元素 |
| `dict.copy()` | 返回一个字典的浅复制 |
| `dict.fromkeys()` | 创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值 |
| `dict.get(key, default=None)` | 返回指定键的值，如果键不在字典中返回 default 设置的默认值 |
| `key in dict` | 如果键在字典dict里返回true，否则返回false |
| `dict.items()` | 以列表返回一个视图对象 |
| `dict.keys()` | 返回一个视图对象 |
| `dict.setdefault(key, default=None)` | 和get()类似，但如果键不存在于字典中，将会添加键并将值设为default |
| `dict.update(dict2)` | 把字典dict2的键/值对更新到dict里 |
| `dict.values()` | 返回一个视图对象 |
| `dict.pop(key[, default])` | 删除字典 key（键）所对应的值，返回被删除的值。 |
| `dict.popitem()` | 返回并删除字典中的最后一对键和值。 |


简单例子：
```python
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False
```












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

# 数据类型转换

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

## 隐式类型转换
在隐式类型转换中，Python 会自动将一种数据类型转换为另一种数据类型，不需要我们去干预。
```python
num_int = 123
num_flo = 1.23

num_new = num_int + num_flo

print("num_int 数据类型为:",type(num_int))
print("num_flo 数据类型为:",type(num_flo))

print("num_new 值为:",num_new)
print("num_new 数据类型为:",type(num_new))
```

## 显式类型转换
`int()` 强制转换为整型：
```python
x = int(1)   # x 输出结果为 1
y = int(2.8) # y 输出结果为 2
z = int("3") # z 输出结果为 3
```

`float()` 强制转换为浮点型：
```python
x = float(1)     # x 输出结果为 1.0
y = float(2.8)   # y 输出结果为 2.8
z = float("3")   # z 输出结果为 3.0
w = float("4.2") # w 输出结果为 4.2
```

`str()` 强制转换为字符串类型：
```python
x = str("s1") # x 输出结果为 's1'
y = str(2)    # y 输出结果为 '2'
z = str(3.0)  # z 输出结果为 '3.0'
```

通常情况下，Python的数据类型的"高低"可以按照如下顺序理解：**布尔（bool）< 整型（int） < 浮点型（float）< 复数（complex）**。这个顺序主要根据数据类型可以表示的信息范围和精度来确定的。

**并非**所有类型的数据都可以被转换成其他任意类型。转换是否可行，主要取决于数据本身是否包含足够的信息来表示目标类型。

- 对于一个非数字字符串（如"Hello"），它无法被转换为一个整数或浮点数，因为这个字符串并不包含任何可以表示一个数字的信息。
- 对于一个列表或元组，它可以被转换为一个集合（如果它的元素是不可变的），但不能被转换为一个整数，因为一个集合或列表中的元素无法合理地表示为一个单独的数字。

# Python 解释器
Python 解释器可不止一种哦，有 CPython、IPython、Jython、PyPy 等。

顾名思义，CPython 就是用 C 语言开发的了，是官方标准实现，拥有良好的生态，所以应用也就最为广泛了。

而 IPython 是在 CPython 的基础之上在交互式方面得到增强的解释器（http://ipython.org/）。

Jython 是专为 Java 平台设计的 Python 解释器（http://www.jython.org/），它把 Python 代码编译成 Java 字节码执行。

PyPy 是 Python 语言（2.7.13和3.5.3）的一种快速、兼容的替代实现（http://pypy.org/），以速度快著称。

# 注释
Python 中单行注释以 `#` 开头，多行注释用三个单引号 `'''` 或者三个双引号 `"""` 将注释括起来。嵌套多行注释会导致语法错误。
```python
'''
这是外部的多行注释
可以包含一些描述性的内容

    '''
    这是尝试嵌套的多行注释
    会导致语法错误
    '''
'''
```
单行注释可以嵌套在多行注释中，而且不会引起语法错误。例如：
```python
'''
这是外部的多行注释
可以包含一些描述性的内容

# 这是内部的单行注释
# 可以嵌套在多行注释中
'''
```
# 运算符
## 算术运算符
以下假设变量 a=10，变量 b=21：

| 运算符 | 描述                     | 实例                                                         |
| ------ | ------------------------ | ------------------------------------------------------------ |
| +      | 加 - 两个对象相加        | a + b 输出结果 31                                            |
| -      | 减 - 得到负数或是一个数减去另一个数 | a - b 输出结果 -11                                           |
| *      | 乘 - 两个数相乘或是返回一个被重复若干次的字符串 | a * b 输出结果 210                                          |
| /      | 除 - x 除以 y             | b / a 输出结果 2.1                                           |
| %      | 取模 - 返回除法的余数    | b % a 输出结果 1                                             |
| **     | 幂 - 返回x的y次幂        | a**b 为10的21次方                                            |
| //     | 取整除 - 往小的方向取整数 | >>> 9//2<br/>4<br/>>>> -9//2<br/>-5 |

## 比较运算符
以下假设变量 a 为 10，变量 b 为20：

以下是转换为 Markdown 格式的表格代码：

| 运算符 | 描述                                                         | 实例                        |
| ------ | ------------------------------------------------------------ | --------------------------- |
| ==     | 等于 - 比较对象是否相等                                      | (a == b) 返回 False。       |
| !=     | 不等于 - 比较两个对象是否不相等                              | (a != b) 返回 True。        |
| >      | 大于 - 返回x是否大于y                                        | (a > b) 返回 False。        |
| <      | 小于 - 返回x是否小于y。所有比较运算符返回1表示真，返回0表示假。这分别与特殊的变量True和False等价。注意，这些变量名的大写。 | (a < b) 返回 True。         |
| >=     | 大于等于 - 返回x是否大于等于y。                              | (a >= b) 返回 False。       |
| <=     | 小于等于 - 返回x是否小于等于y。                              | (a <= b) 返回 True。        |

## 赋值运算符
以下假设变量a为10，变量b为20：

<img width="1023" height="713" alt="image" src="https://github.com/user-attachments/assets/f131f307-eaa2-4ec7-a3ab-94aff6515f15" />

`n := len(a)` 这行代码的作用是计算 `a` 列表的长度，并将结果赋值给变量 `n`。这样，`n` 就可以在 `if` 语句中直接使用，而不需要先单独赋值，然后再在 `if` 中判断。

## 位运算符
按位运算符是把数字看作二进制来进行计算的。Python中的按位运算法则如下：

下表中变量 a 为 60，b 为 13二进制格式如下：
```python
a = 0011 1100

b = 0000 1101

-----------------

a&b = 0000 1100

a|b = 0011 1101

a^b = 0011 0001

~a  = 1100 0011
```

| 运算符 | 描述                                                         | 实例                                                     |
| ------ | ------------------------------------------------------------ | -------------------------------------------------------- |
| &      | 按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0 | (a & b) 输出结果 12 ，二进制解释:  0000 1100             |
| \|     | 按位或运算符：只要对应的二个二进制位有一个为1时，结果位就为1。 | (a \| b) 输出结果 61 ，二进制解释:  0011 1101            |
| ^      | 按位异或运算符：当两对应的二进制位相异时，结果为1            | (a ^ b) 输出结果 49 ，二进制解释:  0011 0001             |
| ~      | 按位取反运算符：对数据的每个二进制位取反,即把1变为0,把0变为1。~x 类似于 -x-1 | (~a) 输出结果 -61 ，二进制解释:  1100 0011， 在一个有符号二进制数的补码形式。 |
| <<     | 左移动运算符：运算数的各二进位全部左移若干位，由 '<<'右边的数指定移动的位数，高位丢弃，低位补0。 | a << 2 输出结果 240 ，二进制解释:  1111 0000             |
| >>     | 右移动运算符：把">>"左边的运算数的各二进位全部右移若干位，">>"右边的数指定移动的位数 | a >> 2 输出结果 15 ，二进制解释:  0000 1111              |

## 逻辑运算符
假设变量 a 为 10, b为 20:

| 运算符 | 逻辑表达式 | 描述                                                         | 实例                        |
| ------ | ---------- | ------------------------------------------------------------ | --------------------------- |
| and    | x and y    | 布尔“与” - 如果 x 为 False，x and y 返回 x 的值，否则返回 y 的计算值。 | (a and b) 返回 20。         |
| or     | x or y     | 布尔“或” - 如果 x 是 True，它返回 x 的值，否则它返回 y 的计算值。 | (a or b) 返回 10。          |
| not    | not x      | 布尔“非” - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。 | not(a and b) 返回 False     |

## 成员运算符

| 运算符 | 描述                                     | 实例                            |
| ------ | ---------------------------------------- | ------------------------------- |
| 在     | 如果在指定的序列中找到值返回 True，否则返回 False。 | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。  |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 | x 不在 y 序列中 , 如果 x 不在 y 序列中返回 True。 |

## 身份运算符
身份运算符用于比较两个对象的存储单元

| 运算符 | 描述                                     | 实例                                                         |
| ------ | ---------------------------------------- | ------------------------------------------------------------ |
| is     | is 判断两个标识符是不是引用自一个对象    | `x is y`，类似 `id(x) == id(y)` ，如果引用的是同一个对象则返回 `True`，否则返回 `False` |
| is not | is not 判断两个标识符是不是引用自不同对象 | `x is not y` ，类似 `id(x) != id(y)`。如果引用的不是同一个对象则返回结果 `True`，否则返回 `False`。 |
注： `id()` 函数用于获取对象内存地址。

> is 与 == 区别：is 用于判断两个变量引用对象是否为同一个， == 用于判断引用变量的值是否相等。
```python
>>>a = [1, 2, 3]
>>> b = a
>>> b is a 
True
>>> b == a
True
>>> b = a[:]
>>> b is a
False
>>> b == a
True
```

## 运算符优先级
以下表格列出了从最高到最低优先级的所有运算符， 相同单元格内的运算符具有相同优先级。 运算符均指二元运算，除非特别指出。

| 运算符 | 描述 |
| ---- | ---- |
| `(expressions...)`, `[expressions...]`, `{key: value...}`, `{expressions...}` | 圆括号的表达式、列表、字典、集合的表达式 |
| `x[index]`, `x[index:index]`, `x(arguments...)`, `x.attribute` | 读取，切片，调用，属性引用 |
| `await x` | `await` 表达式 |
| `**` | 乘方(指数) |
| `+x`, `-x`, `~x` | 正，负，按位非 NOT |
| `*`, `@`, `/`, `//`, `%` | 乘，矩阵乘，除，整除，取余 |
| `+`， `-` | 加和减 |
| `<<`, `>>` | 移位 |
| `&` | 按位与 AND |
| `^` | 按位异或 XOR |
| `|` | 按位或 OR |
| `in`, `not in`, `is`, `is not`, `<`, `<=`, `>`, `>=`, `!=`, `==` | 比较运算，包括成员检测和标识号检测 |
| `not x` | 逻辑非 NOT |
| `and` | 逻辑与 AND |
| `or` | 逻辑或 OR |
| `if -- else` | 条件表达式 |
| `lambda` | `lambda` 表达式 |
| `:=` | 赋值表达式 |

# 条件控制
## if 语句
一般形式如下所示：
```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

在 Python 中没有 `switch...case` 语句，但在 Python3.10 版本添加了 `match...case`

match 后的对象会依次与 case 后的内容进行匹配，如果匹配成功，则执行匹配到的表达式，否则直接跳过，`_` 可以匹配一切。
```python
match subject:
    case <pattern_1>:
        <action_1>
    case <pattern_2>:
        <action_2>
    case <pattern_3>:
        <action_3>
    case _:
        <action_wildcard>
```
`case _`: 类似于 C 和 Java 中的 `default:`，当其他 case 都无法匹配时，匹配这条，保证永远会匹配成功。
```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"

mystatus=400
print(http_error(400))
```
一个 case 也可以设置多个匹配条件，条件使用 ｜ 隔开，例如：
```python
...
    case 401|403|404:
        return "Not allowed"
```
- match语句后跟一个表达式，然后使用case语句来定义不同的模式。
- case后跟一个模式，可以是具体值、变量、通配符等。
- 可以使用if关键字在case中添加条件。

# 循环语句
Python 中的循环语句有 for 和 while。Python 中没有 do..while 循环。

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

语法格式如下：
```python
while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

for 循环可以遍历任何可迭代对象，如一个列表或者一个字符串。

for循环的一般格式如下：
```python
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```
如果在循环过程中遇到了 break 语句，则会中断循环，此时不会执行 else 子句。

可以结合 range() 和 len() 函数以遍历一个序列的索引,如下所示:
```python
>>>a = ['Google', 'Baidu', 'Runoob', 'Taobao', 'QQ']
>>> for i in range(len(a)):
...     print(i, a[i])
... 
0 Google
1 Baidu
2 Runoob
3 Taobao
4 QQ
>>>
```

## break 和 continue 语句及循环中的 else 子句
break 语句可以跳出 for 和 while 的循环体。如果你从 for 或 while 循环中终止，任何对应的循环 else 块将不执行。

continue 语句被用来告诉 Python 跳过当前循环块中的剩余语句，然后继续进行下一轮循环。
<img width="425" height="447" alt="image" src="https://github.com/user-attachments/assets/d9712325-71f2-4d38-9007-22bf41fbe1a3" />
<img width="480" height="452" alt="image" src="https://github.com/user-attachments/assets/d9aa62a7-a5b2-4faf-9fd7-44a3ce104686" />
<img width="708" height="798" alt="image" src="https://github.com/user-attachments/assets/4530656e-1e46-46b2-9b24-686c2e1c95c3" />
<img width="540" height="291" alt="image" src="https://github.com/user-attachments/assets/4d1c9d88-e905-44f3-b307-b2acb6e0101a" />

# 推导式
 推导式是一种独特的数据处理方式，可以从一个数据序列构建另一个新的数据序列的结构体。

 ## 列表推导式
 格式为：
 ```python
[表达式 for 变量 in 列表] 
[out_exp_res for out_exp in input_list]

或者 

[表达式 for 变量 in 列表 if 条件]
[out_exp_res for out_exp in input_list if condition]
 ```
- out_exp_res：列表生成元素表达式，可以是有返回值的函数。
- for out_exp in input_list：迭代 input_list 将 out_exp 传入到 out_exp_res 表达式中。
- if condition：条件语句，可以过滤列表中不符合条件的值。

过滤掉长度小于或等于3的字符串列表，并将剩下的转换成大写字母：
```python
>>> names = ['Bob','Tom','alice','Jerry','Wendy','Smith']
>>> new_names = [name.upper()for name in names if len(name)>3]
>>> print(new_names)
['ALICE', 'JERRY', 'WENDY', 'SMITH']
```

## 字典推导式
基本格式：
```python
{ key_expr: value_expr for value in collection }

或

{ key_expr: value_expr for value in collection if condition }
```

使用字符串及其长度创建字典：
```python
listdemo = ['Google','Runoob', 'Taobao']
# 将列表中各字符串值为键，各字符串的长度为值，组成键值对
>>> newdict = {key:len(key) for key in listdemo}
>>> newdict
{'Google': 6, 'Runoob': 6, 'Taobao': 6}
```

提供三个数字，以三个数字为键，三个数字的平方为值来创建字典：
```python
>>> dic = {x: x**2 for x in (2, 4, 6)}
>>> dic
{2: 4, 4: 16, 6: 36}
>>> type(dic)
<class 'dict'>
```

## 集合推导式
基本格式：
```python
{ expression for item in Sequence }
或
{ expression for item in Sequence if conditional }
```

计算数字 1,2,3 的平方数：
```python
>>> setnew = {i**2 for i in (1,2,3)}
>>> setnew
{1, 4, 9}
```

判断不是 abc 的字母并输出：
```python
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'d', 'r'}
>>> type(a)
<class 'set'>
```

## 元组推导式（生成器表达式）
元组推导式可以利用 range 区间、元组、列表、字典和集合等数据类型，快速生成一个满足指定需求的元组。元组推导式返回的结果是一个生成器对象。基本格式：
```python
(expression for item in Sequence )
或
(expression for item in Sequence if conditional )
```

生成一个包含数字 1~9 的元组：
```python
>>> a = (x for x in range(1,10))
>>> a
<generator object <genexpr> at 0x7faf6ee20a50>  # 返回的是生成器对象

>>> tuple(a)       # 使用 tuple() 函数，可以直接将生成器对象转换成元组
(1, 2, 3, 4, 5, 6, 7, 8, 9)
```

## 进阶
语法格式：
```python
结果值1 if 判断条件 else 结果2  for 变量名 in 原列表
```

```python
list1 = ['python', 'test1', 'test2']
list2 = [word.title() if word.startswith('p') else word.upper() for word in list1]
print(list2)
```
输出结果：
```python
['Python', 'TEST1', 'TEST2']
```

# 迭代器与生成器
## 迭代器
迭代是 Python 最强大的功能之一，是访问集合元素的一种方式。
迭代器是一个可以记住遍历的位置的对象。
迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。
迭代器有两个基本的方法：`iter()` 和 `next()`。
字符串，列表或元组对象都可用于创建迭代器：
```python
>>> list=[1,2,3,4]
>>> it = iter(list)    # 创建迭代器对象
>>> print (next(it))   # 输出迭代器的下一个元素
1
>>> print (next(it))
2
>>>
```
迭代器对象可以使用常规for语句进行遍历：
```python
#!/usr/bin/python3
 
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it:
    print (x, end=" ")
```
也可以使用 next() 函数：
```python
#!/usr/bin/python3
 
import sys         # 引入 sys 模块
 
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
 
while True:
    try:
        print (next(it))
    except StopIteration:
        sys.exit()
```

### 创建一个迭代器
把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

__iter__() 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 __next__() 方法并通过 StopIteration 异常标识迭代的完成。

__next__() 方法会返回下一个迭代器对象。

创建一个返回数字的迭代器，初始值为 1，逐步递增 1：
```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    x = self.a
    self.a += 1
    return x
 
myclass = MyNumbers()
myiter = iter(myclass)
 
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
print(next(myiter))
```

输出结果为：
```python
1
2
3
4
5
```

### StopIteration
StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 __next__() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。

在 20 次迭代后停止执行：
```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
 
  def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
 
myclass = MyNumbers()
myiter = iter(myclass)
 
for x in myiter:
  print(x)
```

## 生成器
在 Python 中，使用了 yield 的函数被称为生成器（generator）。

yield 是一个关键字，用于定义生成器函数，生成器函数是一种特殊的函数，可以在迭代过程中逐步产生值，而不是一次性返回所有结果。

跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

当在生成器函数中使用 yield 语句时，函数的执行将会暂停，并将 yield 后面的表达式作为当前迭代的值返回。

然后，每次调用生成器的 next() 方法或使用 for 循环进行迭代时，函数会从上次暂停的地方继续执行，直到再次遇到 yield 语句。这样，生成器函数可以逐步产生值，而不需要一次性计算并返回所有结果。

**yield 就像一个可以暂停和恢复的 return。当函数执行到 yield 时，它会返回 yield 后面的值，并暂停函数的执行，保存当前所有的运行信息。 当下一次通过 next() 或 for 循环调用它时，它会从上次暂停的地方继续执行。**

调用一个生成器函数，返回的是一个迭代器对象。

下面是一个简单的示例，展示了生成器函数的使用：
```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1
 
# 创建生成器对象
generator = countdown(5)
 
# 通过迭代生成器获取值
print(next(generator))  # 输出: 5
print(next(generator))  # 输出: 4
print(next(generator))  # 输出: 3
 
# 使用 for 循环迭代生成器
for value in generator:
    print(value)  # 输出: 2 1
```
以上实例中，countdown 函数是一个生成器函数。它使用 yield 语句逐步产生从 n 到 1 的倒数数字。在每次调用 yield 语句时，函数会返回当前的倒数值，并在下一次调用时从上次暂停的地方继续执行。

通过创建生成器对象并使用 next() 函数或 for 循环迭代生成器，我们可以逐步获取生成器函数产生的值。在这个例子中，我们首先使用 next() 函数获取前三个倒数值，然后通过 for 循环获取剩下的两个倒数值。

生成器函数的优势是它们可以按需生成值，避免一次性生成大量数据并占用大量内存。此外，生成器还可以与其他迭代工具（如for循环）无缝配合使用，提供简洁和高效的迭代方式。

使用 yield 实现斐波那契数列：
```python
#!/usr/bin/python3
 
import sys
 
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n): 
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
 
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        sys.exit()
```

## 为什么需要迭代器和生成器？
1. 节省内存: 这是最核心的优势。对于非常大的数据集，如果一次性将所有数据加载到内存中（例如，创建一个巨大的列表），可能会耗尽系统内存。而迭代器和生成器采用“惰性计算”或“按需生成”的方式，只在需要时才生成下一个值，因此在内存中始终只保留一个元素。 这使得处理大型文件或无限序列成为可能。

2. 提高效率: 由于数据是按需生成的，程序可以更快地开始处理第一个数据项，而无需等待所有数据都被生成。

3. 代码更简洁优雅: 生成器提供了一种非常简洁的方式来实现迭代器模式，而无需编写一个完整的类并实现 __iter__ 和 __next__ 方法。 这使得代码更易于阅读和维护。

4. 提供统一的迭代方式: 迭代器为所有序列和非序列类型（如字典、集合）提供了一种统一的遍历方式。 for 循环的底层工作原理就是基于迭代器协议的。

迭代器与生成器的主要区别:
| 特性 | 迭代器 (Iterator) | 生成器 (Generator) |
| :--- | :--- | :--- |
| **实现方式** | 通常通过实现一个带有 `__iter__()` 和 `__next__()` 方法的类来创建。 | 通过带有 `yield` 关键字的函数或生成器表达式来创建。 |
| **代码复杂度** | 相对复杂，需要编写一个类。 | 非常简洁，语法更简单。 |
| **本质关系** | 生成器是迭代器的一种特殊、更方便的实现。 所有的生成器都是迭代器，但反之不成立。 | - |
| **数据来源** | 通常是遍历一个已经存在的容器（如列表）。 | 动态地“生成”数据，数据不是预先存在的。 |

例子:
遍历一个二叉树（前序遍历）:
```python
class TreeNode:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right

def preorder_traversal(node):
    """使用生成器进行前序遍历，代码非常直观。"""
    if node is not None:
        yield node.value
        # 'yield from' 是一个强大的语法，可以把另一个生成器的所有值yield出去
        yield from preorder_traversal(node.left)
        yield from preorder_traversal(node.right)

# 构建一个树:
#      1
#     / \
#    2   3
#   /   / \
#  4   5   6
root = TreeNode(1, 
              left=TreeNode(2, left=TreeNode(4)),
              right=TreeNode(3, left=TreeNode(5), right=TreeNode(6)))

print("二叉树前序遍历结果:")
for value in preorder_traversal(root):
    print(value, end=" ") # 输出: 1 2 4 3 5 6

```
**为什么用生成器好？**

代码简洁：递归生成器写起来几乎和标准的递归函数一样简单，避免了手动管理栈的复杂性。yield from 语法更是让代码优雅地处理递归生成。

状态管理：Python自动为你保存和恢复函数的状态（在哪个节点、下一步该去左边还是右边），你无需操心。

# with 关键字
with 关键字为我们提供了一种优雅的方式来处理文件操作、数据库连接等需要明确释放资源的场景。with 是 Python 中的一个关键字，用于上下文管理协议（Context Management Protocol）。它简化了资源管理代码，特别是那些需要明确释放或清理的资源（如文件、网络连接、数据库连接等）。

## with 语句的优势
- 自动资源释放：确保资源在使用后被正确关闭
- 代码简洁：减少样板代码
- 异常安全：即使在代码块中发生异常，资源也会被正确释放
- 可读性强：明确标识资源的作用域

## 基本语法
```python
with expression [as variable]:
    # 代码块
```

最常见的 with 语句应用是文件操作：
```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
# 文件已自动关闭
```
等价于传统的：
```python
file = open('example.txt', 'r')
try:
    content = file.read()
    # 处理文件内容
finally:
    file.close()
```

### 执行流程

<img width="1344" height="1238" alt="image" src="https://github.com/user-attachments/assets/75a59a59-9db1-49d8-8eb0-426a04c312a6" />

## 实际应用场景
### 文件操作
```python
# 同时打开多个文件
with open('input.txt', 'r') as infile, open('output.txt', 'w') as outfile:
    content = infile.read()
    outfile.write(content.upper())
```
###  数据库连接
```python
import sqlite3

with sqlite3.connect('database.db') as conn:
    cursor = conn.cursor()
    cursor.execute('SELECT * FROM users')
    results = cursor.fetchall()
# 连接自动关闭
```
### 线程锁
```python
import threading

lock = threading.Lock()

with lock:
    # 临界区代码
    print("这段代码是线程安全的")
```
### 临时修改系统状态
```python
import decimal

with decimal.localcontext() as ctx:
    ctx.prec = 42  # 临时设置高精度
    # 执行高精度计算
# 精度恢复原设置
```

## 创建自定义的上下文管理器
### 类实现方式
```python
class Timer:
    def __enter__(self):
        import time
        self.start = time.time()
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        import time
        self.end = time.time()
        print(f"耗时: {self.end - self.start:.2f}秒")
        return False

# 使用示例
with Timer() as t:
    # 执行一些耗时操作
    sum(range(1000000))
```

### 使用 contextlib 模块
```python
from contextlib import contextmanager

@contextmanager
def tag(name):
    print(f"<{name}>")
    yield
    print(f"</{name}>")

# 使用示例
with tag("h1"):
    print("这是一个标题")
```


# 函数
## 定义一个函数
规则：

- 函数代码块以 def 关键词开头，后接函数标识符名称和圆括号 ()。
- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以冒号 : 起始，并且缩进。
- return [表达式] 结束函数，选择性地返回一个值给调用方，不带表达式的 return 相当于返回 None。

<img width="634" height="391" alt="image" src="https://github.com/user-attachments/assets/09f88a75-0d7e-47d7-8e3e-d6c0a5dd0b1f" />

## 参数传递
在 python 中，类型属于对象，对象有不同类型的区分，变量是没有类型的。

### 可更改(mutable)与不可更改(immutable)对象
在 python 中，strings, tuples, 和 numbers 是不可更改的对象，而 list,dict 等则是可以修改的对象。

python 函数的参数传递：

- 不可变类型：类似 C++ 的值传递，如整数、字符串、元组。如 fun(a)，传递的只是 a 的值，没有影响 a 对象本身。如果在 fun(a) 内部修改 a 的值，则是新生成一个 a 的对象。
- 可变类型：类似 C++ 的引用传递，如 列表，字典。如 fun(la)，则是将 la 真正的传过去，修改后 fun 外部的 la 也会受影响

python 中一切都是对象，严格意义我们不能说值传递还是引用传递，我们应该说传不可变对象和传可变对象。

```python
def change(a):
    print(a)
    print(id(a))
    a = 2
    print(a)
    print(id(a))

a = 1
print(a)
print(id(a))
change(a)
print(a)
print(id(a))
```
输出：
```python
1
2074164816176
1
2074164816176
2
2074164816208
1
2074164816176
```

```python
#!/usr/bin/python3
 
# 可写函数说明
def changeme( mylist ):
   "修改传入的列表"
   mylist.append([1,2,3,4])
   print ("函数内取值: ", mylist)
   return
 
# 调用changeme函数
mylist = [10,20,30]
changeme( mylist )
print ("函数外取值: ", mylist)
```
输出：
```python
函数内取值:  [10, 20, 30, [1, 2, 3, 4]]
函数外取值:  [10, 20, 30, [1, 2, 3, 4]]
```

## 参数类型
### 必需参数
必需参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。
```python
#!/usr/bin/python3
 
#可写函数说明
def printme( str ):
   "打印任何传入的字符串"
   print (str)
   return
 
# 调用 printme 函数，不加参数会报错
printme()
```

### 关键字参数
关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。

使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。

```python
#!/usr/bin/python3
 
#可写函数说明
def printinfo( name, age ):
   "打印任何传入的字符串"
   print ("名字: ", name)
   print ("年龄: ", age)
   return
 
#调用printinfo函数
printinfo( age=50, name="runoob" )
```

### 默认参数
调用函数时，如果没有传递参数，则会使用默认参数。
```python
#!/usr/bin/python3
 
#可写函数说明
def printinfo( name, age = 35 ):
   "打印任何传入的字符串"
   print ("名字: ", name)
   print ("年龄: ", age)
   return
 
#调用printinfo函数
printinfo( age=50, name="runoob" )
print ("------------------------")
printinfo( name="runoob" )
```

### 不定长参数
可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述 2 种参数不同，声明时不会命名。基本语法如下：
```python
def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]

```

加了星号 * 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。
```python
#!/usr/bin/python3
  
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )
```

还有一种就是参数带两个星号 **基本语法如下：
```python
def functionname([formal_args,] **var_args_dict ):
   "函数_文档字符串"
   function_suite
   return [expression]
```

加了两个星号 ** 的参数会以字典的形式导入。
```python
#!/usr/bin/python3
  
# 可写函数说明
def printinfo( arg1, **vardict ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vardict)
 
# 调用printinfo 函数
printinfo(1, a=2,b=3)
```
输出结果：
```python
输出: 
1
{'a': 2, 'b': 3}

```

声明函数时，参数中星号 `*` 可以单独出现，如果单独出现星号 `*`，则星号 `*` 后的参数必须用关键字传入：
```python
>>> def f(a,b,*,c):
...     return a+b+c
... 
>>> f(1,2,3)   # 报错
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: f() takes 2 positional arguments but 3 were given
>>> f(1,2,c=3) # 正常
6
>>>
```

## 匿名函数
Python 使用 lambda 来创建匿名函数。

所谓匿名，意即不再使用 def 语句这样标准的形式定义一个函数。

- lambda 只是一个表达式，函数体比 def 简单很多。
- lambda 的主体是一个表达式，而不是一个代码块。仅仅能在 lambda 表达式中封装有限的逻辑进去。
- lambda 函数拥有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数。
- 虽然 lambda 函数看起来只能写一行，却不等同于 C 或 C++ 的内联函数，内联函数的目的是调用小函数时不占用栈内存从而减少函数调用的开销，提高代码的执行速度。

### 语法
```python
lambda [arg1 [,arg2,.....argn]]:expression
```

例子：
```python
x = lambda a : a + 10
print(x(5)) # 15
```

```python
#!/usr/bin/python3
 
# 可写函数说明
sum = lambda arg1, arg2: arg1 + arg2
 
# 调用sum函数
print ("相加后的值为 : ", sum( 10, 20 )) # 相加后的值为 :  30
print ("相加后的值为 : ", sum( 20, 20 )) # 相加后的值为 :  40
```

可以将匿名函数封装在一个函数内，这样可以使用同样的代码来创建多个匿名函数。
```python
def myfunc(n):
  return lambda a : a * n
 
mydoubler = myfunc(2)
mytripler = myfunc(3)
 
print(mydoubler(11)) # 22
print(mytripler(11)) # 33
```

## return 语句
不带参数值的 return 语句返回 None。

## 强制位置参数
Python3.8 新增了一个函数形参语法 / 用来指明函数形参必须使用指定位置参数，不能使用关键字参数的形式。

在以下的例子中，形参 a 和 b 必须使用指定位置参数，c 或 d 可以是位置形参或关键字形参，而 e 和 f 要求为关键字形参:
```python
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
```
正确的:
```python
f(10, 20, 30, d=40, e=50, f=60)
```
错误:
```python
f(10, b=20, c=30, d=40, e=50, f=60)   # b 不能使用关键字参数的形式
f(10, 20, 30, 40, 50, f=60)           # e 必须使用关键字参数的形式
```

# 装饰器
装饰器（decorators）是 Python 中的一种高级功能，它允许你动态地修改函数或类的行为。

装饰器是一种函数，它接受一个函数作为参数，并返回一个新的函数或修改原来的函数。

<img width="320" height="564" alt="image" src="https://github.com/user-attachments/assets/a963e42d-b1df-4a31-a4d9-fc7a179b3ac6" />

装饰器的语法使用 @decorator_name 来应用在函数或方法上。Python 还提供了一些内置的装饰器，比如 @staticmethod 和 @classmethod，用于定义静态方法和类方法。

应用场景：
- 日志记录: 装饰器可用于记录函数的调用信息、参数和返回值。
- 性能分析: 可以使用装饰器来测量函数的执行时间。
- 权限控制: 装饰器可用于限制对某些函数的访问权限。
- 缓存: 装饰器可用于实现函数结果的缓存，以提高性能。

## 内置装饰器
Python 提供了一些内置的装饰器，例如：

1. @staticmethod: 将方法定义为静态方法，不需要实例化类即可调用。

2. @classmethod: 将方法定义为类方法，第一个参数是类本身（通常命名为 cls）。

3. @property: 将方法转换为属性，使其可以像属性一样访问。

```python
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method.")

    @classmethod
    def class_method(cls):
        print(f"This is a class method of {cls.__name__}.")

    @property
    def name(self):
        return self._name

    @name.setter
    def name(self, value):
        self._name = value

# 使用
MyClass.static_method()
MyClass.class_method()

obj = MyClass()
obj.name = "Alice"
print(obj.name)
```

## 多个装饰器的堆叠
可以将多个装饰器堆叠在一起，它们会按照从下到上的顺序依次应用。例如：
```python
def decorator1(func):
    def wrapper():
        print("Decorator 1")
        func()
    return wrapper

def decorator2(func):
    def wrapper():
        print("Decorator 2")
        func()
    return wrapper

@decorator1
@decorator2
def say_hello():
    print("Hello!")

say_hello()
```
输出：
```python
Decorator 1
Decorator 2
Hello!
```

# 数据结构
## 遍历
在字典中遍历时，关键字和对应的值可以使用 items() 方法同时解读出来：
```python
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

在序列中遍历时，索引位置和对应值可以使用 enumerate() 函数同时得到：
```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```

同时遍历两个或更多的序列，可以使用 zip() 组合：
```python
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```

要反向遍历一个序列，首先指定这个序列，然后调用 reversed() 函数：
```python
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```

要按顺序遍历一个序列，使用 sorted() 函数返回一个已排序的序列，并不修改原值：
```python
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```

# 模块
一个模块只会被导入一次，不管你执行了多少次 import。这样可以防止导入模块被一遍又一遍地执行。

如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用 __name__ 属性来使该程序块仅在该模块自身运行时执行。
```python
#!/usr/bin/python3
# Filename: using_name.py

if __name__ == '__main__':
   print('程序自身在运行')
else:
   print('我来自另一模块')

```
> 说明：__name__ 与 __main__ 底下是双下划线， _ _ 是这样去掉中间的那个空格。

# 输入和输出
## 输出格式美化
Python两种输出值的方式: 表达式语句和 print() 函数。

第三种方式是使用文件对象的 write() 方法，标准输出文件可以用 sys.stdout 引用。

如果你希望输出的形式更加多样，可以使用 str.format() 函数来格式化输出值。

如果你希望将输出的值转成字符串，可以使用 repr() 或 str() 函数来实现。

- str()： 函数返回一个用户易读的表达形式。
- repr()： 产生一个解释器易读的表达形式。

```python
>>> s = 'Hello, Runoob'
>>> str(s)
'Hello, Runoob'
>>> repr(s)
"'Hello, Runoob'"
>>> str(1/7)
'0.14285714285714285'
>>> x = 10 * 3.25
>>> y = 200 * 200
>>> s = 'x 的值为： ' + repr(x) + ',  y 的值为：' + repr(y) + '...'
>>> print(s)
x 的值为： 32.5,  y 的值为：40000...
>>> #  repr() 函数可以转义字符串中的特殊字符
... hello = 'hello, runoob\n'
>>> hellos = repr(hello)
>>> print(hellos)
'hello, runoob\n'
>>> # repr() 的参数可以是 Python 的任何对象
... repr((x, y, ('Google', 'Runoob')))
"(32.5, 40000, ('Google', 'Runoob'))"
```

str.format() 的基本使用如下:
```python
>>> print('{}网址： "{}!"'.format('菜鸟教程', 'www.runoob.com'))
菜鸟教程网址： "www.runoob.com!"
```
括号及其里面的字符 (称作格式化字段) 将会被 format() 中的参数替换。

在括号中的数字用于指向传入对象在 format() 中的位置，如下所示：
```python
>>> print('{0} 和 {1}'.format('Google', 'Runoob'))
Google 和 Runoob
>>> print('{1} 和 {0}'.format('Google', 'Runoob'))
Runoob 和 Google
```
如果在 format() 中使用了关键字参数, 那么它们的值会指向使用该名字的参数。
```python
>>> print('{name}网址： {site}'.format(name='菜鸟教程', site='www.runoob.com'))
菜鸟教程网址： www.runoob.com
```
位置及关键字参数可以任意的结合:
```python
>>> print('站点列表 {0}, {1}, 和 {other}。'.format('Google', 'Runoob', other='Taobao'))
站点列表 Google, Runoob, 和 Taobao。
```
下面的例子将 Pi 保留到小数点后三位：
```python
>>> import math
>>> print('常量 PI 的值近似为 {0:.3f}。'.format(math.pi))
常量 PI 的值近似为 3.142。
```
如果你有一个很长的格式化字符串, 而你不想将它们分开, 那么在格式化时通过变量名而非位置会是很好的事情。

最简单的就是传入一个字典, 然后使用方括号 [] 来访问键值 :
```python
>>> table = {'Google': 1, 'Runoob': 2, 'Taobao': 3}
>>> print('Runoob: {0[Runoob]:d}; Google: {0[Google]:d}; Taobao: {0[Taobao]:d}'.format(table))
Runoob: 2; Google: 1; Taobao: 3
```
也可以通过在 table 变量前使用 ** 来实现相同的功能：
```python
>>> table = {'Google': 1, 'Runoob': 2, 'Taobao': 3}
>>> print('Runoob: {Runoob:d}; Google: {Google:d}; Taobao: {Taobao:d}'.format(**table))
Runoob: 2; Google: 1; Taobao: 3
```

## 读取键盘输入
Python 提供了 input() 内置函数从标准输入读入一行文本，默认的标准输入是键盘。
```python
#!/usr/bin/python3

str = input("请输入：");
print ("你输入的内容是: ", str)
```

## 读和写文件
open() 将会返回一个 file 对象，基本语法格式如下:
```python
open(filename, mode)
```
- filename：包含了你要访问的文件名称的字符串值。
- mode：决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。

<img width="1022" height="940" alt="image" src="https://github.com/user-attachments/assets/96da3af2-bdfe-4002-9284-a7fd3efcaa3a" />

<img width="1182" height="702" alt="image" src="https://github.com/user-attachments/assets/53835fad-e27a-4a17-af41-3aa73538305e" />

<img width="1018" height="370" alt="image" src="https://github.com/user-attachments/assets/8b27fefe-22b9-45a0-a2f5-656357df0c2c" />

[关于文件的更多操作](https://www.runoob.com/python3/python3-file-methods.html)


# 异常处理
## try/except
异常捕捉可以使用 `try/except` 语句。
<img width="1394" height="556" alt="image" src="https://github.com/user-attachments/assets/a1addbf1-ffd9-4e6b-8012-e9dbf213e705" />

以下例子中，让用户输入一个合法的整数，但是允许用户中断这个程序（使用 Control-C 或者操作系统提供的方法）。用户中断的信息会引发一个 KeyboardInterrupt 异常。
```python
while True:
    try:
        x = int(input("请输入一个数字: "))
        break
    except ValueError:
        print("您输入的不是数字，请再次尝试输入！")
```
一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

处理程序将只针对对应的 try 子句中的异常进行处理，而不是其他的 try 的处理程序中的异常。

一个except子句可以同时处理多个异常，这些异常将被放在一个括号里成为一个元组，例如:
```python
except (RuntimeError, TypeError, NameError):
    pass
```
最后一个except子句可以忽略异常的名称，它将被当作通配符使用。你可以使用这种方法打印一个错误信息，然后再次把异常抛出。
```python
import sys

try:
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except:
    print("Unexpected error:", sys.exc_info()[0])
    raise
```

## try/except...else

try/except 语句还有一个可选的 else 子句，如果使用这个子句，那么必须放在所有的 except 子句之后。

else 子句将在 try 子句**没有发生任何异常**的时候执行。

<img width="1394" height="783" alt="image" src="https://github.com/user-attachments/assets/658125bf-cf39-4cfa-a4c8-fb63cacde101" />

异常处理并不仅仅处理那些直接发生在 try 子句中的异常，而且还能处理子句中调用的函数（甚至间接调用的函数）里抛出的异常。例如:
```python
>>> def this_fails():
        x = 1/0
   
>>> try:
        this_fails()
    except ZeroDivisionError as err:
        print('Handling run-time error:', err)
   
Handling run-time error: int division or modulo by zero
```

## try-finally 语句
try-finally 语句无论是否发生异常都将执行最后的代码。
<img width="1394" height="1000" alt="image" src="https://github.com/user-attachments/assets/55e0fc6c-033d-461a-944b-618ec45ef6bd" />

## 抛出异常
Python 使用 raise 语句抛出一个指定的异常。

raise语法格式如下：
```python
raise [Exception [, args [, traceback]]]
```
<img width="1394" height="311" alt="image" src="https://github.com/user-attachments/assets/c076c303-3ef1-45d9-bed9-cd19cf6ea34d" />

## 用户自定义异常
可以通过创建一个新的异常类来拥有自己的异常。异常类继承自 Exception 类，可以直接继承，或者间接继承，例如:
```python
>>> class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
   
>>> try:
        raise MyError(2*2)
    except MyError as e:
        print('My exception occurred, value:', e.value)
   
My exception occurred, value: 4
>>> raise MyError('oops!')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
__main__.MyError: 'oops!'
```

# 面向对象
## 面向对象技术简介
- 类(Class): 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- 方法：类中定义的函数。
- 类变量：类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
- 数据成员：类变量或者实例变量用于处理类及其实例对象的相关的数据。
- 方法重写：如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
- 局部变量：定义在方法中的变量，只作用于当前实例的类。
- 实例变量：在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。
- 继承：即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
- 实例化：创建一个类的实例，类的具体对象。
- 对象：通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

## self 代表类的实例，而非类
类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self。
```python
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```
self 不是 python 关键字，我们把他换成 runoob 也是可以正常执行的:
```python
class Test:
    def prt(runoob):
        print(runoob)
        print(runoob.__class__)
 
t = Test()
t.prt()
```

## 继承
Python 同样支持类的继承，如果一种语言不支持继承，类就没有什么意义。派生类的定义如下所示:
```python
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```
子类（派生类 DerivedClassName）会继承父类（基类 BaseClassName）的属性和方法。

BaseClassName（实例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用:
```python
class DerivedClassName(modname.BaseClassName):
```

```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
 
 
s = student('ken',10,60,3)
s.speak()
```

## 多继承
Python同样有限的支持多继承形式。多继承的类定义形如下例:
```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```

需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。
```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
#另一个类，多继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
 
#多继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中参数位置排前父类的方法
```

输出结果为：`我叫 Tim，我是一个演说家，我演讲的主题是 Python`


## 方法重写
如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法，实例如下：
```python
#!/usr/bin/python3
 
class Parent:        # 定义父类
   def myMethod(self):
      print ('调用父类方法')
 
class Child(Parent): # 定义子类
   def myMethod(self):
      print ('调用子类方法')
 
c = Child()          # 子类实例
c.myMethod()         # 子类调用重写方法
super(Child,c).myMethod() #用子类对象调用父类已被覆盖的方法
```
super() 函数是用于调用父类(超类)的一个方法。

## 类属性与方法
### 类的私有属性
`__private_attrs`：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 `self.__private_attrs`。

### 类的私有方法
`__private_method`：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。`self.__private_methods`。

```python
#!/usr/bin/python3
 
class JustCounter:
    __secretCount = 0  # 私有变量
    publicCount = 0    # 公开变量
 
    def count(self):
        self.__secretCount += 1
        self.publicCount += 1
        print (self.__secretCount)
 
counter = JustCounter()
counter.count()
counter.count()
print (counter.publicCount)
print (counter.__secretCount)  # 报错，实例不能访问私有变量
```

```python
#!/usr/bin/python3
 
class Site:
    def __init__(self, name, url):
        self.name = name       # public
        self.__url = url   # private
 
    def who(self):
        print('name  : ', self.name)
        print('url : ', self.__url)
 
    def __foo(self):          # 私有方法
        print('这是私有方法')
 
    def foo(self):            # 公共方法
        print('这是公共方法')
        self.__foo()
 
x = Site('菜鸟教程', 'www.runoob.com')
x.who()        # 正常输出
x.foo()        # 正常输出
x.__foo()      # 报错
```

<img width="1018" height="278" alt="image" src="https://github.com/user-attachments/assets/59ce9509-bef4-4d8f-8292-feed9b73eb5b" />

## 运算符重载
Python同样支持运算符重载，我们可以对类的专有方法进行重载，实例如下：
```python
#!/usr/bin/python3
 
class Vector:
   def __init__(self, a, b):
      self.a = a
      self.b = b
 
   def __str__(self):
      return 'Vector (%d, %d)' % (self.a, self.b)
   
   def __add__(self,other):
      return Vector(self.a + other.a, self.b + other.b)
 
v1 = Vector(2,10)
v2 = Vector(5,-2)
print (v1 + v2)
```

# 命名空间喝作用域
命名空间(Namespace)是从名称到对象的映射，大部分的命名空间都是通过 Python 字典来实现的。

命名空间提供了在项目中避免名字冲突的一种方法。各个命名空间是独立的，没有任何关系的，所以一个命名空间中不能有重名，但不同的命名空间是可以重名而没有任何影响。

我们举一个计算机系统中的例子，一个文件夹(目录)中可以包含多个文件夹，每个文件夹中不能有相同的文件名，但不同文件夹中的文件可以重名。
<img width="544" height="372" alt="image" src="https://github.com/user-attachments/assets/0c07e3c6-b36f-4580-9b5b-3a4929140481" />

[具体可以查看此处](https://www.runoob.com/python3/python3-namespace-scope.html)

# [Python3 实例](https://www.runoob.com/python3/python3-examples.html)

