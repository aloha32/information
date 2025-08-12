# 简介
Python 是一个高层次的结合了解释性、编译性、互动性和面向对象的脚本语言。

# 基础语法
默认情况下，Python3 源码文件以 UTF-8 编码，所有字符串都是 unicode 字符串。
## 标识符
第一个字符必须以字母（a-z, A-Z）或下划线 `_` 。其他的部分由字母、数字和下划线组成。**大小写敏感**，count 和 Count 是不同的标识符。

## 保留关键字
保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：
```
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

