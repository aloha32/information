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
| in     | 如果在指定的序列中找到值返回 True，否则返回 False。 | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。  |
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
