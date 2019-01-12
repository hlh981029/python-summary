# 作者

**Guido van Rossum 吉多·范罗苏姆（1956年1月31日 荷兰）**

Python是“龟叔”在1989年圣诞节期间，为了打发无聊的圣诞节而编写的一个编程语言。之所以选中Python作为程序的名字，是因为他是BBC电视剧——蒙提·派森的飞行马戏团的爱好者。Python社区的人称他为“终身仁慈独裁者（BDFL）”。

# 注释

## 单行注释

Python中单行注释以`#`开头，例如：

```python
# 这是一个注释
print("Hello, World!") # 这也是一个注释 
```

## 多行注释
多行注释用三个单引号`'''`或者三个双引号`"""`将注释括起来，例如：
- 单引号（`'''`）

    ```python
    '''
    这是多行注释，用三个单引号
    这是多行注释，用三个单引号 
    '''
    ```

- 双引号（`"""`）
    
    ```python
    """
    这是多行注释，用三个双引号
    这是多行注释，用三个双引号 
    """
    ```

# 基本数据类型

## 标准数据类型

Python3 中有六个标准的数据类型：
- Number（数字）
    - `int`、`float`、`bool`、`complex`（复数）
- String（字符串）
    - `str`
- List（列表）
    - `list`
- Tuple（元组）
    - `tuple`
- Set（集合）
    - `set`
- Dictionary（字典）
    - `dict`

## 可变与不可变

### 可变 mutable

- 包括：`list`, `dict`, `set`
- **修改mutable变量时直接修改变量内容**
- 变量赋值`a=[1,2,3,4]`后再赋值`a[0]=0`则是将列表`a`的第一个元素值更改，本身`a`没有动，只是其内部的一部分值被修改了。

    ```python
    >>> a = [1,2,3,4]
    >>> id(a)
    4538793608
    >>> a[0] = 0
    >>> id(a)
    4538793608
    ```

### 不可变 immutable
- 包括：`int`, `float`, `bool`, `complex`, `str`, `tuple`, `frozenset`
- **修改immutable变量时修改指向的地址**
- 变量赋值`a=1`后再赋值`a=2`，这里实际是新生成一个`int`值对象`2`，再让`a`指向它，而`1`被丢弃，不是改变`a`的值，相当于新生成了`a`。

    ```python
    >>> a = 1
    >>> id(a)
    4519444512
    >>> a = 2
    >>> id(a)
    4519444544
    ```

### 函数调用传递参数时

- **不可变类型**：类似c++的值传递，`fun(a)`传递的只是`a`的值，没有影响`a`对象本身。比如在`fun(a)`内部修改`a`的值，只是修改另一个复制的对象，不会影响`a`本身。
- **可变类型**：类似c++的引用传递，`fun(a)`则是将`a`真正的传过去，修改后`fun`外部的`a`也会受影响。

## 查询变量类型

内置的 `type()` 函数可以用来查询变量所指的对象类型。

```python
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

此外还可以用 `isinstance()` 来判断：

```python
>>> a = 111
>>> isinstance(a, int)
True
```

`isinstance` 和 `type` 的区别在于：
- `type()`不会认为子类是一种父类类型。
- `isinstance()`会认为子类是一种父类类型。

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

## 数据类型转换

| 函数 | 描述 |
| --- | --- |
| [int(x [,base])](http://www.runoob.com/python3/python-func-int.html) | 将x转换为一个整数 |
| [float(x)](http://www.runoob.com/python3/python-func-float.html) | 将x转换到一个浮点数 |
| [complex(real [,imag])](http://www.runoob.com/python3/python-func-complex.html)   | 创建一个复数 |
| [str(x)](http://www.runoob.com/python3/python-func-str.html) | 将对象 x 转换为字符串 |
| [repr(x)](http://www.runoob.com/python3/python-func-repr.html) | 将对象 x 转换为表达式字符串 |
| [eval(str)](http://www.runoob.com/python3/python-func-eval.html) | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
| [tuple(s)](http://www.runoob.com/python3//python3/python3-func-tuple.html) | 将序列 s 转换为一个元组 |
| [list(s)](http://www.runoob.com/python3/python3-att-list-list.html) | 将序列 s 转换为一个列表 |
| [set(s)](http://www.runoob.com/python3/python-func-set.html) | 转换为可变集合 |
| [dict(d)](http://www.runoob.com/python3/python-func-dict.html) | 创建一个字典。d 必须是一个序列 (key,value)元组。 |
| [frozenset(s)](http://www.runoob.com/python3/python-func-frozenset.html) | 转换为不可变集合 |
| [chr(x)](http://www.runoob.com/python3/python-func-chr.html) |   将一个整数转换为一个字符 |
| [ord(x)](http://www.runoob.com/python3/python-func-ord.html) |  将一个字符转换为它的整数值 |
| [hex(x)](http://www.runoob.com/python3/python-func-hex.html) |   将一个整数转换为一个十六进制字符串 |
| [oct(x)](http://www.runoob.com/python3/python-func-oct.html) |  将一个整数转换为一个八进制字符串 |


# 基本运算符

## 算术运算符

<table><tbody>
<tr><th>运算符</th><th>描述</th><th>实例</th></tr>
<tr><td>**</td><td>幂 - 返回x的y次幂</td><td> a**b 为10的21次方</td></tr>
<tr><td>//</td><td>取整除 - 向下取接近除数的整数</td><td>

```python
>>> 9//2
4
>>> -9//2
-5
```

</td></tr></tbody></table>

## 比较运算符

- `==`
- `!=`
- `>`
- `<`
- `>=`
- `<=`

## 成员运算符

| 运算符 | 描述                                                    |
| ------ | ------------------------------------------------------- |
| in     | 如果在指定的序列中找到值返回 True，否则返回 False。     |
| not in | 如果在指定的序列中没有找到值返回 True，否则返回 False。 |

## 身份运算符

身份运算符用于比较两个对象的存储单元

| 运算符 | 描述                                        | 实例                                                                                         |
| ------ | ------------------------------------------- | -------------------------------------------------------------------------------------------- |
| is     | is 是判断两个标识符是不是引用自一个对象     | `x is y`类似`id(x) == id(y)`， 如果引用的是同一个对象则返回 True，否则返回 False              |
| is not | is not 是判断两个标识符是不是引用自不同对象 | `x is not y`类似`id(a) != id(b)`。如果引用的不是同一个对象则返回结果 True，否则返回 False。 |

## 优先级

|运算符 | 描述|
|---|---|
|** | 指数 (最高优先级)|
|~ + - | 按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@)|
|* / % // | 乘，除，取模和取整除|
|+ - | 加法减法|
|>> << | 右移，左移运算符|
|& | 位 'AND'|
|^ | | 位运算符|
|<= < > >= | 比较运算符|
|<> == != | 等于运算符|
|= %= /= //= -= += *= **= | 赋值运算符|
|is is not | 身份运算符|
|in not in | 成员运算符|
|and or not | 逻辑运算符|

# 数字

## 表示形式

| int | float | complex |
| --- | --- | --- |
| `10` | `0.0` | `3.14j` |
| `100` | `15.20` | `45.j` |
| `-786` | `-21.9` | `9.322e-36j` |
| `080` | `32.3+e18` | `.876j` |
| `-0490` | `-90.` | `-.6545+0J` |
| `-0x260` | `-32.54e100` | `3e+26J` |
| `0x69` | `70.2-E12` | `4.53e-7j` |

## 数学函数

| 函数 | 返回值 ( 描述 ) |
| --- | --- |
| abs(x) | 返回数字的绝对值，如abs(-10) 返回 10 |
| ceil(x) | 返回数字的上入整数，如math.ceil(4.1) 返回 5 |
| exp(x) | 返回e的x次幂(ex),如math.exp(1) 返回2.718281828459045 |
| fabs(x) | 返回数字的绝对值，如math.fabs(-10) 返回10.0 |
| floor(x) | 返回数字的下舍整数，如math.floor(4.9)返回 4 |
| log(x) | 如math.log(math.e)返回1.0,math.log(100,10)返回2.0 |
| log10(x) | 返回以10为基数的x的对数，如math.log10(100)返回 2.0 |
| max(x1, x2,...) | 返回给定参数的最大值，参数可以为序列。 |
| min(x1, x2,...) | 返回给定参数的最小值，参数可以为序列。 |
| modf(x) | 返回x的整数部分与小数部分，两部分的数值符号与x相同，整数部分以浮点型表示。 |
| pow(x, y) | x**y 运算后的值。 |
| round(x [,n]) | 返回浮点数x的四舍五入值，如给出n值，则代表舍入到小数点后的位数。 |
| sqrt(x) | 返回数字x的平方根。 |

## 随机数函数

- 需要random模块

| 函数 | 描述 |
| --- | --- |
| choice(seq) | 从序列的元素中随机挑选一个元素，比如random.choice(range(10))，从0到9中随机挑选一个整数。 |
| randrange ([start,] stop [,step]) | 从[start, stop)范围内，按指定基数递增的集合中获取一个随机数，start缺省值为0，step缺省值为1 |
| random() | 随机生成下一个实数，它在[0,1)范围内。 |
| seed([x]) | 改变随机数生成器的种子seed。如果你不了解其原理，你不必特别去设定seed，Python会帮你选择seed。 |
| shuffle(lst) | 将序列的所有元素随机排序 |
| uniform(x, y) | 随机生成下一个实数，它在[x,y]范围内。 |

# 字符串

## 编码与解码

```python
>>> a = '你好'
>>> type(a)
<class 'str'>
>>> a.encode()
b'\xe4\xbd\xa0\xe5\xa5\xbd'
>>> b = a.encode()
>>> type(b)
<class 'bytes'>
>>> b.decode()
'你好'
>>> bytes.decode(b)
'你好'
```
<span id="index-and-slice"></span>

## 索引与切片

| 语法 | 说明 |
| --- | --- |
| `s[i]` | `i`th item of `s`, origin 0 |
| `s[i:j]` | slice of `s` from `i` to `j` |
| `s[i:j:k]` | slice of `s` from `i` to `j` with step `k` |

**左闭右开**

If `i` or `j` is negative, the index is relative to the end of sequence `s`: `len(s) + i` or `len(s) + j` is substituted. But note that `-0` is still `0`.

The slice of `s` from `i` to `j` is defined as the sequence of items with index `k` such that `i <= k < j`. If `i` or `j` is greater than `len(s)`, use `len(s)`. If `i` is omitted or `None`, use `0`. If `j` is omitted or `None`, use `len(s)`. If `i` is greater than or equal to `j`, the slice is empty.

The slice of `s` from `i` to `j` with step `k` is defined as the sequence of items with index `x = i + n*k` such that `0 <= n < (j-i)/k`. In other words, the indices are `i, i+k, i+2*k, i+3*k` and so on, stopping when `j` is reached (but never including `j`). When `k` is positive, `i` and `j` are reduced to `len(s)` if they are greater. When `k` is negative, `i` and `j` are reduced to `len(s) - 1` if they are greater. If `i` or `j` are omitted or `None`, they become “end” values (which end depends on the sign of `k`). Note, `k` cannot be zero. If `k` is None, it is treated like `1`.

``` python
s = '0123456789'
s[0]		# '0'
s[0:1]		# '0'
s[0:2]		# '01'
s[:2]		# '01'
s[:]		# '0123456789'
s[0:]		# '0123456789'
s[0:-1]		# '012345678'
s[-1:]		# '9'
s[-1:0]		# ''
s[-1:0:-1]	# '987654321'
s[-1:0:-2]	# '97531'
s[0:-1:2]	# '02468'
```
## 内建函数

<table class="reference">
<tbody>
<tr><th style="width:5%">序号</th><th>方法及描述</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-string-capitalize.html">capitalize()</a><br>将字符串的第一个字符转换为大写</td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-string-center.html">center(width, fillchar)</a><br>返回一个指定的宽度 width 居中的字符串，fillchar 为填充的字符，默认为空格。</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-string-count.html">count(str, beg= 0,end=len(string))</a><br>返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-string-decode.html">bytes.decode(encoding="utf-8", errors="strict")</a><br>Python3 中没有 decode 方法，但我们可以使用 bytes 对象的 decode() 方法来解码给定的 bytes 对象，这个 bytes 对象可以由 str.encode() 来编码返回。</td></tr>
<tr><td>5</td><td><a href="http://www.runoob.com/python3/python3-string-encode.html">encode(encoding='UTF-8',errors='strict')</a><br>以 encoding 指定的编码格式编码字符串，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace'</td></tr>
<tr><td>6</td><td><a href="http://www.runoob.com/python3/python3-string-endswith.html">endswith(suffix, beg=0, end=len(string))</a><br>检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False.</td></tr>
<tr><td>7</td><td><a href="http://www.runoob.com/python3/python3-string-expandtabs.html">expandtabs(tabsize=8)</a><br>把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8 。</td></tr>
<tr><td>8</td><td><a href="http://www.runoob.com/python3/python3-string-find.html">find(str, beg=0 end=len(string))</a><br>检测 str 是否包含在字符串中，如果指定范围 beg 和 end ，则检查是否包含在指定范围内，如果包含返回开始的索引值，否则返回-1</td></tr>
<tr><td>9</td><td><a href="http://www.runoob.com/python3/python3-string-index.html">index(str, beg=0, end=len(string))</a><br>跟find()方法一样，只不过如果str不在字符串中会报一个异常.</td></tr>
<tr><td>10</td><td><a href="http://www.runoob.com/python3/python3-string-isalnum.html">isalnum()</a><br>如果字符串至少有一个字符并且所有字符都是字母或数字则返回 True,否则返回 False</td></tr>
<tr><td>11</td><td><a href="http://www.runoob.com/python3/python3-string-isalpha.html">isalpha()</a><br>如果字符串至少有一个字符并且所有字符都是字母则返回 True,否则返回 False</td></tr>
<tr><td>12</td><td><a href="http://www.runoob.com/python3/python3-string-isdigit.html">isdigit()</a><br>如果字符串只包含数字则返回 True 否则返回 False..</td></tr>
<tr><td>13</td><td><a href="http://www.runoob.com/python3/python3-string-islower.html">islower()</a><br>如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是小写，则返回 True，否则返回 False</td></tr>
<tr><td>14</td><td><a href="http://www.runoob.com/python3/python3-string-isnumeric.html">isnumeric()</a><br>如果字符串中只包含数字字符，则返回 True，否则返回 False</td></tr>
<tr><td>15</td><td><a href="http://www.runoob.com/python3/python3-string-isspace.html">isspace()</a><br>如果字符串中只包含空白，则返回 True，否则返回 False.</td></tr>
<tr><td>16</td><td><a href="http://www.runoob.com/python3/python3-string-istitle.html">istitle()</a><br>如果字符串是标题化的(见 title())则返回 True，否则返回 False</td></tr>
<tr><td>17</td><td><a href="http://www.runoob.com/python3/python3-string-isupper.html">isupper()</a><br>如果字符串中包含至少一个区分大小写的字符，并且所有这些(区分大小写的)字符都是大写，则返回 True，否则返回 False</td></tr>
<tr><td>18</td><td><a href="http://www.runoob.com/python3/python3-string-join.html">join(seq)</a><br>以指定字符串作为分隔符，将 seq 中所有的元素(的字符串表示)合并为一个新的字符串</td></tr>
<tr><td>19</td><td><a href="http://www.runoob.com/python3/python3-string-len.html">len(string)</a><br>返回字符串长度</td></tr>
<tr><td>20</td><td><a href="http://www.runoob.com/python3/python3-string-ljust.html">ljust(width[, fillchar])</a><br>返回一个原字符串左对齐,并使用 fillchar 填充至长度 width 的新字符串，fillchar 默认为空格。</td></tr>
<tr><td>21</td><td><a href="http://www.runoob.com/python3/python3-string-lower.html">lower()</a><br>转换字符串中所有大写字符为小写.</td></tr>
<tr><td>22</td><td><a href="http://www.runoob.com/python3/python3-string-lstrip.html">lstrip()</a><br>截掉字符串左边的空格或指定字符。</td></tr>
<tr><td>23</td><td><a href="http://www.runoob.com/python3/python3-string-maketrans.html">maketrans()</a><br>创建字符映射的转换表，对于接受两个参数的最简单的调用方式，第一个参数是字符串，表示需要转换的字符，第二个参数也是字符串表示转换的目标。</td></tr>
<tr><td>24</td><td><a href="http://www.runoob.com/python3/python3-string-max.html">max(str)</a><br>返回字符串 str 中最大的字母。</td></tr>
<tr><td>25</td><td><a href="http://www.runoob.com/python3/python3-string-min.html">min(str)</a><br>返回字符串 str 中最小的字母。</td></tr>
<tr><td>26</td><td><a href="http://www.runoob.com/python3/python3-string-replace.html">replace(old, new [, max])</a><br>把 将字符串中的 str1 替换成 str2,如果 max 指定，则替换不超过 max 次。</td></tr>
<tr><td>27</td><td><a href="http://www.runoob.com/python3/python3-string-rfind.html">rfind(str, beg=0,end=len(string))</a><br>类似于 find()函数，不过是从右边开始查找.</td></tr>
<tr><td>28</td><td><a href="http://www.runoob.com/python3/python3-string-rindex.html">rindex( str, beg=0, end=len(string))</a><br>类似于 index()，不过是从右边开始.</td></tr>
<tr><td>29</td><td><a href="http://www.runoob.com/python3/python3-string-rjust.html">rjust(width,[, fillchar])</a><br>返回一个原字符串右对齐,并使用fillchar(默认空格）填充至长度 width 的新字符串</td></tr>
<tr><td>30</td><td><a href="http://www.runoob.com/python3/python3-string-rstrip.html">rstrip()</a><br>删除字符串字符串末尾的空格.</td></tr>
<tr><td>31</td><td><a href="http://www.runoob.com/python3/python3-string-split.html">split(str="", num=string.count(str))</a><br>num=string.count(str))以 str 为分隔符截取字符串，如果 num 有指定值，则仅截取 num+1 个子字符串</td></tr>
<tr><td>32</td><td><a href="http://www.runoob.com/python3/python3-string-splitlines.html">splitlines([keepends])</a><br>按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数 keepends 为 False，不包含换行符，如果为 True，则保留换行符。</td></tr>
<tr><td>33</td><td><a href="http://www.runoob.com/python3/python3-string-startswith.html">startswith(substr, beg=0,end=len(string))</a><br>检查字符串是否是以指定子字符串 substr 开头，是则返回 True，否则返回 False。如果beg 和 end 指定值，则在指定范围内检查。</td></tr>
<tr><td>34</td><td><a href="http://www.runoob.com/python3/python3-string-strip.html">strip([chars])</a><br>在字符串上执行 lstrip()和 rstrip()</td></tr>
<tr><td>35</td><td><a href="http://www.runoob.com/python3/python3-string-swapcase.html">swapcase()</a><br>将字符串中大写转换为小写，小写转换为大写</td></tr>
<tr><td>36</td><td><a href="http://www.runoob.com/python3/python3-string-title.html">title()</a><br>返回"标题化"的字符串,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle())</td></tr>
<tr><td>37</td><td><a href="http://www.runoob.com/python3/python3-string-translate.html">translate(table, deletechars="")</a><br>根据 str 给出的表(包含 256 个字符)转换 string 的字符,要过滤掉的字符放到 deletechars 参数中</td></tr>
<tr><td>38</td><td><a href="http://www.runoob.com/python3/python3-string-upper.html">upper()</a><br>	转换字符串中的小写字母为大写</td></tr>
<tr><td>39</td><td><a href="http://www.runoob.com/python3/python3-string-zfill.html">zfill (width)</a><br>返回长度为 width 的字符串，原字符串右对齐，前面填充0</td></tr>
<tr><td>40</td><td><a href="http://www.runoob.com/python3/python3-string-isdecimal.html">isdecimal()</a><br>检查字符串是否只包含十进制字符，如果是返回 true，否则返回 false。</td></tr>
</tbody></table>

# 列表

## 定义

Lists may be constructed in several ways:

- Using a pair of square brackets to denote the empty list: `[]`
- Using square brackets, separating items with commas: `[a]`, `[a, b, c]`
- Using a list comprehension (列表生成式): `[x for x in iterable]`
- Using the type constructor: `list()` or `list(iterable)`
> The constructor builds a list whose items are the same and in the same order as iterable’s items. iterable may be either a sequence, a container that supports iteration, or an iterator object. If iterable is already a list, a copy is made and returned, similar to iterable`[:]`. For example, `list('abc')` returns `['a', 'b', 'c']` and `list( (1, 2, 3) )` returns `[1, 2, 3]`. If no argument is given, the constructor creates a new empty list, `[]`.

## 索引与切片
- 同[字符串的索引与切片](#index-and-slice)

## 删除

```python
>>> a=[0,1,2,3,4,5,6,7,8,9]
>>> del a[9]
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8]
>>> del a[7:9]
>>> a
[0, 1, 2, 3, 4, 5, 6]
```

## `append()`与`extend()`
列表的 `extent()` 与 `+=` 功能相同
```python
>>> a = (1, 2, 3)
>>> b = [1, 2, 3]
>>> b.append(a)
>>> b
[1, 2, 3, (1, 2, 3)]
>>> b.extend(a)
>>> b
[1, 2, 3, (1, 2, 3), 1, 2, 3]
>>> b += a
>>> b
[1, 2, 3, (1, 2, 3), 1, 2, 3, 1, 2, 3]
```

## 运算符

列表对 + 和 * 的操作符与字符串相似。+ 号用于组合列表，* 号用于重复列表。

| 表达式 | 结果 | 描述 |
| --- | --- | --- |
| `len([1, 2, 3])` | `3` | 长度 |
| `[1, 2, 3] + [4, 5, 6]` | `[1, 2, 3, 4, 5, 6]` | 组合 |
| `['Hi!'] * 4` | `['Hi!', 'Hi!', 'Hi!', 'Hi!']` | 重复 |
| `3 in [1, 2, 3]` | `True` | 元素是否存在于列表中 |
| `for x in [1, 2, 3]: print(x, end=" ")` | `1 2 3` | 迭代 |

## 函数

<table class="reference">
<tbody><tr>
<th style="width:5%">序号</th><th style="width:95%">函数</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-list-len.html">len(list)</a><br>列表元素个数</td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-list-max.html">max(list)</a><br>返回列表元素最大值</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-list-min.html">min(list)</a><br>返回列表元素最小值</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-list-list.html">list(seq)</a><br>将元组转换为列表</td></tr>
</tbody></table>

## 方法

<table class="reference">
<tbody><tr>
<th style="width:5%">序号</th><th style="width:95%">方法</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-list-append.html">list.append(obj)</a><br>在列表末尾添加新的对象</td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-list-count.html">list.count(obj)</a><br>统计某个元素在列表中出现的次数</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-list-extend.html">list.extend(seq)</a><br>在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-list-index.html">list.index(obj)</a><br>从列表中找出某个值第一个匹配项的索引位置</td></tr>
<tr><td>5</td><td><a href="http://www.runoob.com/python3/python3-att-list-insert.html">list.insert(index, obj)</a><br>将对象插入列表</td></tr>
<tr><td>6</td><td><a href="http://www.runoob.com/python3/python3-att-list-pop.html">list.pop([index=-1])</a><br>移除列表中的一个元素（默认最后一个元素），并且返回该元素的值</td></tr>
<tr><td>7</td><td><a href="http://www.runoob.com/python3/python3-att-list-remove.html">list.remove(obj)</a><br>移除列表中某个值的第一个匹配项</td></tr>
<tr><td>8</td><td><a href="http://www.runoob.com/python3/python3-att-list-reverse.html">list.reverse()</a><br>反向列表中元素</td></tr>
<tr><td>9</td><td><a href="http://www.runoob.com/python3/python3-att-list-sort.html">	list.sort(cmp=None, key=None, reverse=False)</a><br>对原列表进行排序</td></tr>
<tr><td>10</td><td><a href="http://www.runoob.com/python3/python3-att-list-clear.html">list.clear()</a><br>清空列表</td></tr>
<tr><td>11</td><td><a href="http://www.runoob.com/python3/python3-att-list-copy.html">list.copy()</a><br>复制列表</td></tr>
</tbody></table>

# 元组

## 定义

Tuples may be constructed in a number of ways:

- Using a pair of parentheses to denote the empty tuple: `()`
- Using a trailing comma for a singleton tuple: `a,` or `(a,)`
- Separating items with commas: `a, b, c` or `(a, b, c)`
- Using the `tuple()` built-in: `tuple()` or `tuple(iterable)`
> The constructor builds a tuple whose items are the same and in the same order as iterable’s items. iterable may be either a sequence, a container that supports iteration, or an iterator object. If iterable is already a tuple, it is returned unchanged. For example, `tuple('abc')` returns `('a', 'b', 'c')` and `tuple( [1, 2, 3] )` returns `(1, 2, 3)`. If no argument is given, the constructor creates a new empty tuple, `()`.

> Note that it is actually the comma which makes a tuple, not the parentheses. The parentheses are optional, except in the empty tuple case, or when they are needed to avoid syntactic ambiguity. For example, f(a, b, c) is a function call with three arguments, while f((a, b, c)) is a function call with a 3-tuple as the sole argument.

## 索引与切片
- 同[字符串的索引与切片](#index-and-slice)

## 修改

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合，如下实例:

```python 
>>> tup1 = (12, 34.56);
>>> tup2 = ('abc', 'xyz')
>>> 
>>> # 以下修改元组元素操作是非法的。
>>> # tup1[0] = 100
>>> 
>>> # 创建一个新的元组
>>> tup3 = tup1 + tup2;
>>> print (tup3)
(12, 34.56, 'abc', 'xyz')
```

## 运算符

与字符串一样，元组之间可以使用 + 号和 * 号进行运算。这就意味着他们可以组合和复制，运算后会生成一个新的元组。

| 表达式 | 结果 | 描述 |
| --- | --- | --- |
| `len((1, 2, 3))` | `3` | 计算元素个数 |
| `(1, 2, 3) + (4, 5, 6)` | `(1, 2, 3, 4, 5, 6)` | 连接 |
| `('Hi!',) * 4` | `('Hi!', 'Hi!', 'Hi!', 'Hi!')` | 复制 |
| `3 in (1, 2, 3)` | `True` | 元素是否存在 |
| `for x in (1, 2, 3): print (x,)` | `1 2 3` | 迭代 |

## 元组与列表相加

```python
>>> a = (1, 2, 3)
>>> b = [1, 2, 3]
>>>
>>> c = a + b
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate tuple (not "list") to tuple
>>> a += b
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate tuple (not "list") to tuple
>>> b += a
>>> b
[1, 2, 3, 1, 2, 3]
```

# 字典

## 定义

Dictionaries can be created by placing a comma-separated list of key: value pairs within braces, for example: `{'jack': 4098, 'sjoerd': 4127}` or `{4098: 'jack', 4127: 'sjoerd'}`, or by the `dict` constructor.

- 键必须是唯一的，但值则不必。  
- 值可以取任何数据类型，但键必须是`hashable`的，如字符串，数字或元组（自定义的类也是`hashable`）。创建时如果同一个键被赋值两次，后一个值会被记住.

> `hashable`  
> An object is hashable if it has a hash value which never changes during its lifetime (it needs a `__hash__()` method), and can be compared to other objects (it needs an `__eq__()` method). Hashable objects which compare equal must have the same hash value.  
> Hashability makes an object usable as a dictionary key and a set member, because these data structures use the hash value internally.   
> All of Python’s immutable built-in objects are hashable; mutable containers (such as lists or dictionaries) are not. Objects which are instances of user-defined classes are hashable by default. They all compare unequal (except with themselves), and their hash value is derived from their id().



```python
>>> a = dict(one=1, two=2, three=3)
>>> b = {'one': 1, 'two': 2, 'three': 3}
>>> c = dict(zip(['one', 'two', 'three'], [1, 2, 3]))
>>> d = dict([('two', 2), ('one', 1), ('three', 3)])
>>> e = dict({'three': 3, 'one': 1, 'two': 2})
>>> a == b == c == d == e
True
```

## 索引

- 取值：`a['key']`
- 赋值：`a['key'] = b`
- 删除：`del a['key']`

## 内置函数

- `len(dict)`：返回元素个数
- `str(dict)`：返回可打印字符串
- `type(dict)`：返回字典类型

## 内置方法

<table class="reference">
<tbody><tr>
<th style="width:5%">序号</th><th style="width:95%">函数及描述</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-clear.html">dict.clear()</a><br>删除字典内所有元素 </td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-copy.html">dict.copy()</a><br>返回一个字典的浅复制</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-fromkeys.html">dict.fromkeys()</a><br> 创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值

```python
>>> seq = ('name', 'age', 'sex')
>>> dict.fromkeys(seq)
{'age': None, 'name': None, 'sex': None}
>>> dict.fromkeys(seq, 10)
{'age': 10, 'name': 10, 'sex': 10}
```

</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-get.html">dict.get(key, default=None)</a><br>返回指定键的值，如果值不在字典中返回default值</td></tr>
<tr><td>5</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-in.html">key in dict</a><br>如果键在字典dict里返回true，否则返回false</td></tr>
<tr><td>6</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-items.html">dict.items()</a><br>以列表返回可遍历的(键, 值) 元组数组</td></tr>
<tr><td>7</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-keys.html">dict.keys()</a><br>返回一个迭代器，可以使用 list() 来转换为列表</td></tr>
<tr><td>8</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-setdefault.html">dict.setdefault(key, default=None)</a><br>和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default</td></tr>
<tr><td>9</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-update.html">dict.update(dict2)</a><br>把字典dict2的键/值对更新到dict里</td></tr>
<tr><td>10</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-values.html">dict.values()</a><br>返回一个迭代器，可以使用 list() 来转换为列表</td></tr>
<tr><td>11</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-pop.html">pop(key[,default])</a><br>删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。否则，返回default值。</td></tr>
<tr><td>12</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-popitem.html"> popitem()</a><br>随机返回并删除字典中的一对键和值(一般删除末尾对)。</td></tr>
</tbody></table>

# 集合

## 定义

There are currently two built-in set types, `set` and `frozenset`. The `set` type is mutable — the contents can be changed using methods like `add()` and `remove()`. Since it is mutable, it has no hash value and cannot be used as either a dictionary key or as an element of another set. The `frozenset` type is immutable and `hashable` — its contents cannot be altered after it is created; it can therefore be used as a dictionary key or as an element of another set.

Non-empty sets (not frozensets) can be created by placing a comma-separated list of elements within braces, for example: `{'jack', 'sjoerd'}`, in addition to the `set` constructor.

The constructors for both classes work the same:

- `set([iterable])`
- `frozenset([iterable])`

Return a new `set` or `frozenset` object whose elements are taken from `iterable`. The elements of a set must be `hashable`. To represent sets of sets, the inner sets must be `frozenset` objects. If `iterable` is not specified, a new empty set is returned.

> `{ }` 创建的是一个空字典，不是集合。

## 内置方法

<table class="reference">
<tbody><tr><th>方法</th><th>描述</th></tr>
<tr><td colspan="2"><code>set</code>与<code>frozenset</code>都可以使用</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-isdisjoint.html" target="_blank">set.isdisjoint(other)</a></td><td>判断两个集合是否包含相同的元素，如果没有返回 True，否则返回 False。</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-issubset.html" target="_blank">set.issubset(other)</a></td><td>判断指定集合是否为该方法参数集合的子集。

```python
# set.issubset(other)
# 等价于
set <= other
# set <= other and set != other
# 等价于
set < other
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-issuperset.html" target="_blank">set.issuperset(other)</a></td><td>判断该方法的参数集合是否为指定集合的子集

```python
# set.issuperset(other)
# 等价于
set >= other
# set >= other and set != other
# 等价于
set > other
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-union.html" target="_blank">set.union(*others)</a></td><td>返回两个集合的并集

```python
# set.union(other, ...)
# 等价于
set | other | ...
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-intersection.html" target="_blank">set.intersection(*others)</a></td><td>返回集合的交集

```python
# set.intersection(other, ...)
# 等价于
set & other & ...
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-difference.html" target="_blank">set.difference(*others)</a></td><td>返回多个集合的差集

```python
# set.difference(other, ...)
# 等价于
set - other - ...
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-symmetric_difference.html" target="_blank">set.symmetric_difference(other)</a></td><td>返回两个集合中不重复的元素集合。

```python
# set.symmetric_difference(other)
# 等价于
set ^ other ^ ...
```

</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-copy.html" target="_blank">set.copy()</a></td><td>拷贝一个集合</td></tr>
<tr><td colspan="2">只有<code>set</code>可以使用</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-update.html" target="_blank">set.update(*others)</a></td><td>给集合添加元素（并），等价于 <code>set |= other | ...</code></td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-intersection_update.html" target="_blank">set.intersection_update(*others)</a></td><td>删除集合中的元素，该元素在指定的集合中不存在（交），等价于 <code>set &= other & ...</code></td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-difference_update.html" target="_blank">set.difference_update(*others)</a></td><td>移除集合中的元素，该元素在指定的集合也存在（差），等价于 <code>set -= other - ...</code></td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-symmetric_difference_update.html" target="_blank">set.symmetric_difference_update(other)</a></td><td>移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中，等价于 <code>set ^= other ^ ...</code></td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-add.html" target="_blank">set.add(elem)</a></td><td>为集合添加元素</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-remove.html" target="_blank">set.remove(elem)</a></td><td>删除集合中指定的元素，不存在抛出异常</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-discard.html" target="_blank">set.discard(elem)</a></td><td>删除集合中指定的元素，不存在不抛出异常</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-pop.html" target="_blank">set.pop()</a></td><td>随机移除元素</td></tr>
<tr><td><a href="http://www.runoob.com/python3/ref-set-clear.html" target="_blank">set.clear()</a></td><td>移除集合中的所有元素</td></tr>
</tbody></table>

# 控制流

## `if` Statements

```python
>>> x = int(input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
...
More
```

There can be zero or more `elif` parts, and the `else` part is optional. The keyword `elif` is short for `else if`, and is useful to avoid excessive indentation. An `if … elif … elif …` sequence is a substitute for the switch or case statements found in other languages.

## `for` Statements

Python’s `for` statement iterates over the items of any sequence (a list or a string), in the order that they appear in the sequence. For example:

```python
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
```

If you need to modify the sequence you are iterating over while inside the loop (for example to duplicate selected items), it is recommended that you first make a copy. Iterating over a sequence does not implicitly make a copy. The slice notation makes this especially convenient:

```python
>>> for w in words[:]:  # Loop over a slice copy of the entire list.
...     if len(w) > 6:
...         words.insert(0, w)
...
>>> words
['defenestrate', 'cat', 'window', 'defenestrate']
```

With `for w in words:`, the example would attempt to create an infinite list, inserting defenestrate over and over again.

## The `range()` Function

If you do need to iterate over a sequence of numbers, the built-in function `range()` comes in handy. It generates arithmetic progressions:

```python
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

The given end point is **never** part of the generated sequence; `range(10)` generates 10 values, the legal indices for items of a sequence of length 10. It is possible to let the range start at another number, or to specify a different increment (even negative; sometimes this is called the ‘step’):

```python
range(5, 10)
   5, 6, 7, 8, 9

range(0, 10, 3)
   0, 3, 6, 9

range(-10, -100, -30)
  -10, -40, -70
```

To iterate over the indices of a sequence, you can combine `range()` and `len()` as follows:

```python
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```

A strange thing happens if you just print a range:

```python
>>> print(range(10))
range(0, 10)
```

In many ways the object returned by `range()` behaves as if it is a list, but in fact it isn’t. It is an object which returns the successive items of the desired sequence when you iterate over it, but it doesn’t really make the list, thus saving space.

We say such an object is `iterable`, that is, suitable as a target for functions and constructs that expect something from which they can obtain successive items until the supply is exhausted. We have seen that the for statement is such an iterator. The function `list()` is another; it creates lists from iterables:

```python
>>> list(range(5))
[0, 1, 2, 3, 4]
```

## `break` and `continue` Statements, and `else` Clauses on Loops

The `break` statement, like in C, breaks out of the innermost enclosing `for` or `while` loop.

Loop statements may have an `else` clause; it is executed when the loop terminates through exhaustion of the list (with `for`) or when the condition becomes false (with `while`), **but not when the loop is terminated by a break statement**. This is exemplified by the following loop, which searches for prime numbers:

```python
>>> for n in range(2, 6):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop fell through without finding a factor
...         print(n, 'is a prime number')
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
```

When used with a loop, the `else` clause has more in common with the `else` clause of a `try` statement than it does that of if statements: a `try` statement’s `else` clause runs when no exception occurs, and a loop’s `else` clause runs when no `break` occurs.

The `continue` statement, also borrowed from C, continues with the next iteration of the loop:

```python
>>> for num in range(2, 6):
...     if num % 2 == 0:
...         print("Found an even number", num)
...         continue
...     print("Found a number", num)
Found an even number 2
Found a number 3
Found an even number 4
Found a number 5
```

## `pass` Statements

The `pass` statement does nothing. It can be used when a statement is required syntactically but the program requires no action. For example:

```python
>>> while True:
...     pass  # Busy-wait for keyboard interrupt (Ctrl+C)
...
```

This is commonly used for creating minimal classes:

```python
>>> class MyEmptyClass:
...     pass
...
```

Another place `pass` can be used is as a place-holder for a function or conditional body when you are working on new code, allowing you to keep thinking at a more abstract level. The pass is silently ignored:

```python
>>> def initlog(*args):
...     pass   # Remember to implement this!
...
```

# 函数

## 方法和函数

- 函数(function)是Python中一个可调用对象(callable), 方法(method)是一种特殊的函数。
- 一个可调用对象是方法和函数，和这个对象无关，仅和这个对象是否与类或实例绑定有关（bound method）。
- 实例方法，在类中未和类绑定，是函数；在实例中，此实例方法与实例绑定，即变成方法。
- 静态方法没有和任何类或实例绑定，所以静态方法是个函数。
- 装饰器不会改变被装饰函数或方法的类型。
- 类实现`__call__`方法,其实例也不会变成方法或函数,依旧是类的实例。
- 使用`callalble()`只能判断对象是否可调用,不能判断是不是函数或方法。
- 判断对象是函数或方法应该使用`type(obj)`。

## 必需参数

必需参数须以正确的顺序传入函数。调用时的数量必须和声明时的一样。

## 默认参数

调用函数时，如果没有传递参数，则会使用默认参数。

```python
def fun(a, b=2):
    pass
```

The default values are evaluated at the point of function definition in the defining scope, so that

```python
i = 5

def f(arg=i):
    print(arg)

i = 6
f()
```

will print 5.

Important warning: The default value is evaluated only once. This makes a difference when the default is a mutable object such as a list, dictionary, or instances of most classes. For example, the following function accumulates the arguments passed to it on subsequent calls:

```python
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
```

This will print

```python
[1]
[1, 2]
[1, 2, 3]
```

If you don’t want the default to be shared between subsequent calls, you can write the function like this instead:

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
```

## 关键字参数

关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。

使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。

Functions can also be called using keyword arguments of the form `kwarg=value`. For instance, the following function:

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")
```

accepts one required argument (`voltage`) and three optional arguments (`state`, `action`, and `type`). This function can be called in any of the following ways:

```python
parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
```

but all the following calls would be invalid:

```python
parrot()                     # required argument missing
parrot(voltage=5.0, 'dead')  # non-keyword argument after a keyword argument
parrot(110, voltage=220)     # duplicate value for the same argument
parrot(actor='John Cleese')  # unknown keyword argument
```

In a function call, keyword arguments must follow positional arguments. All the keyword arguments passed must match one of the arguments accepted by the function (e.g. `actor` is not a valid argument for the `parrot` function), and their order is not important. This also includes non-optional arguments (e.g. `parrot(voltage=1000)` is valid too). No argument may receive a value more than once. Here’s an example that fails due to this restriction:

```python
>>>
>>> def function(a):
...     pass
...
>>> function(0, a=0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: function() got multiple values for keyword argument 'a'
```

## 不定长参数

你可能需要一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述 2 种参数不同，声明时不会命名。基本语法如下：
```python
def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]
```

加了星号 * 的参数会以元组(`tuple`)的形式导入，存放所有未命名的变量参数。

```python
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )
```

输出结果：

```python
输出: 
70
(60, 50)
```

如果在函数调用时没有指定参数，它就是一个空元组。我们也可以不向函数传递未命名的变量。如下：

```python
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   for var in vartuple:
      print (var)
   return
 
# 调用printinfo 函数
printinfo( 10 )
printinfo( 70, 60, 50 )
```

输出结果：

```python
输出:
10
输出:
70
60
50
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

声明函数时，参数中星号 * 可以单独出现，例如:

```python
def f(a,b,*,c):
    return a+b+c
```
如果单独出现星号 * 后的参数必须用关键字传入。

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

## 参数组合
在Python中定义函数，可以用必选参数、默认参数、可变参数、关键字参数和命名关键字参数，这5种参数都可以组合使用。但是请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数。

## Unpacking Argument Lists

The reverse situation occurs when the arguments are already in a list or tuple but need to be unpacked for a function call requiring separate positional arguments. For instance, the built-in `range()` function expects separate start and stop arguments. If they are not available separately, write the function call with the *-operator to unpack the arguments out of a list or tuple:

```python
>>>
>>> list(range(3, 6))            # normal call with separate arguments
[3, 4, 5]
>>> args = [3, 6]
>>> list(range(*args))            # call with arguments unpacked from a list
[3, 4, 5]
```

In the same fashion, dictionaries can deliver keyword arguments with the **-operator:

```python
>>>
>>> def parrot(voltage, state='a stiff', action='voom'):
...     print("-- This parrot wouldn't", action, end=' ')
...     print("if you put", voltage, "volts through it.", end=' ')
...     print("E's", state, "!")
...
>>> d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
>>> parrot(**d)
-- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised !
```

## 匿名函数（Lambda 表达式）

python 使用 lambda 来创建匿名函数。

所谓匿名，意即不再使用 def 语句这样标准的形式定义一个函数。

- 实际上是一个函数定义的语法糖。
- lambda 只是一个表达式，函数体比 def 简单很多。
- lambda的主体是一个表达式，而不是一个代码块。仅仅能在lambda表达式中封装有限的逻辑进去。
- lambda 函数拥有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数。
- 虽然lambda函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。

### 语法

lambda 函数的语法只包含一个语句，如下：
  
```python
lambda [arg1 [,arg2,.....argn]]:expression
```

### 用法

```python
>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)
42
>>> f(1)
43
```

The above example uses a lambda expression to return a function. Another use is to pass a small function as an argument:

```python
>>>
>>> pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
>>> pairs.sort(key=lambda pair: pair[1])
>>> pairs
[(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```

## 变量作用域

Python 中，程序的变量并不是在哪个位置都可以访问的，访问权限决定于这个变量是在哪里赋值的。

变量的作用域决定了在哪一部分程序可以访问哪个特定的变量名称。Python的作用域一共有4种，分别是：

- L （Local） 局部作用域
- E （Enclosing） 闭包函数外的函数中
- G （Global） 全局作用域
- B （Built-in） 内建作用域

以 L –> E –> G –>B 的规则查找，即：在局部找不到，便会去局部外的局部找（例如闭包），再找不到就会去全局找，再者去内建中找。

```python
x = int(2.9)  # 内建作用域
 
g_count = 0  # 全局作用域
def outer():
    o_count = 1  # 闭包函数外的函数中
    def inner():
        i_count = 2  # 局部作用域
```

Python 中只有模块（module），类（class）以及函数（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的，也就是说这些语句内定义的变量，外部也可以访问，如下代码：

```python
>>> if True:
...  msg = 'I am from Runoob'
... 
>>> msg
'I am from Runoob'
>>> 
```

实例中 msg 变量定义在 if 语句块中，但外部还是可以访问的。

如果将 msg 定义在函数中，则它就是局部变量，外部不能访问：

```python
>>> def test():
...     msg_inner = 'I am from Runoob'
... 
>>> msg_inner
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'msg_inner' is not defined
>>> 
```

从报错的信息上看，说明了 msg_inner 未定义，无法使用，因为它是局部变量，只有在函数内可以使用。

## 全局变量和局部变量

定义在函数内部的变量拥有一个局部作用域，定义在函数外的拥有全局作用域。

局部变量只能在其被声明的函数内部访问，而全局变量可以在整个程序范围内访问。调用函数时，所有在函数内声明的变量名称都将被加入到作用域中。如下实例：

```python
total = 0 # 这是一个全局变量
# 可写函数说明
def sum( arg1, arg2 ):
    #返回2个参数的和."
    total = arg1 + arg2 # total在这里是局部变量.
    print ("函数内是局部变量 : ", total)
    return total
 
#调用sum函数
sum( 10, 20 )
print ("函数外是全局变量 : ", total)
```

以上实例输出结果：

```python
函数内是局部变量 :  30
函数外是全局变量 :  0
```

global 和 nonlocal关键字
当内部作用域想修改外部作用域的变量时，就要用到global和nonlocal关键字了。

以下实例修改全局变量 num：

```python
num = 1
def fun1():
    global num  # 需要使用 global 关键字声明
    print(num) 
    num = 123
    print(num)
fun1()
print(num)
```

以上实例输出结果：

```python
1
123
123
```

如果要修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量则需要 nonlocal 关键字了，如下实例：

```python 
def outer():
    num = 10
    def inner():
        nonlocal num   # nonlocal关键字声明
        num = 100
        print(num)
    inner()
    print(num)
outer()
```

以上实例输出结果：

```python
100
100
```

This is an example demonstrating how to reference the different scopes and namespaces, and how `global` and `nonlocal` affect variable binding:
```python
def scope_test():
    def do_local():
        spam = "local spam"

    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"

    def do_global():
        global spam
        spam = "global spam"

    spam = "test spam"
    do_local()
    print("After local assignment:", spam)
    do_nonlocal()
    print("After nonlocal assignment:", spam)
    do_global()
    print("After global assignment:", spam)

scope_test()
print("In global scope:", spam)
```

The output of the example code is:

```python
After local assignment: test spam
After nonlocal assignment: nonlocal spam
After global assignment: nonlocal spam
In global scope: global spam
```

另外有一种特殊情况，假设下面这段代码被运行：

```python
a = 10
def test():
    a = a + 1
    print(a)
test()
```

以上程序执行，报错信息如下：

```python
Traceback (most recent call last):
  File "test.py", line 7, in <module>
    test()
  File "test.py", line 5, in test
    a = a + 1
UnboundLocalError: local variable 'a' referenced before assignment
```

错误信息为局部作用域引用错误，因为 test 函数中的 a 使用的是局部，未定义，无法修改。

修改 a 为全局变量，通过函数参数传递，可以正常执行输出结果为：

```python
a = 10
def test(a):
    a = a + 1
    print(a)
test(a)
```

# 类

## 简介

- 类(Class): 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- 方法：类中定义的函数。
- 类变量：类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
- 数据成员：类变量或者实例变量用于处理类及其实例对象的相关的数据。
- 方法重写：如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
- 局部变量：定义在方法中的变量，只作用于当前实例的类。
- 实例变量：在类的声明中，属性是用变量来表示的。这种变量就称为实例变量，是在类声明的内部但是在类的其他成员方法之外声明的。
- 继承：即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
- 实例化：创建一个类的实例，类的具体对象。
- 对象：通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

## Class Definition Syntax

```python
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```

## Class Objects

Class objects support two kinds of operations: attribute references（属性引用） and instantiation（实例化）.

### Attribute References（属性引用）

If the class definition looked like this:

```python
class MyClass:
    i = 12345

    def f(self):
        return 'hello world'
```

then `MyClass.i` and `MyClass.f` are valid attribute references, returning an integer and a function object, respectively. Class attributes can also be assigned to, so you can change the value of `MyClass.i` by assignment.

### Instantiation（实例化）

Class instantiation uses function notation. Just pretend that the class object is a parameterless function that returns a new instance of the class. For example (assuming the above class):

```python
x = MyClass()
```

creates a new instance of the class and assigns this object to the local variable x.

### 构造函数

The instantiation operation (“calling” a class object) creates an empty object. Many classes like to create objects with instances customized to a specific initial state. Therefore a class may define a special method named `__init__()`, like this:

```python
def __init__(self):
    self.data = []
```

When a class defines an `__init__()` method, class instantiation automatically invokes `__init__()` for the newly-created class instance.

Of course, the `__init__()` method may have arguments for greater flexibility. In that case, arguments given to the class instantiation operator are passed on to `__init__()`. For example,

```python
>>>
>>> class Complex:
...     def __init__(self, realpart, imagpart):
...         self.r = realpart
...         self.i = imagpart
...
>>> x = Complex(3.0, -4.5)
>>> x.r, x.i
(3.0, -4.5)
```

## Instance Objects

Now what can we do with instance objects? The only operations understood by instance objects are attribute references. There are two kinds of valid attribute names, data attributes（数据属性） and methods（方法）.

data attributes correspond to “instance variables” in Smalltalk, and to “data members” in C++. Data attributes need not be declared; like local variables, they spring into existence when they are first assigned to. For example, if `x` is the instance of `MyClass` created above, the following piece of code will print the value 16, without leaving a trace:

```python
x.counter = 1
while x.counter < 10:
    x.counter = x.counter * 2
print(x.counter)
del x.counter
```

The other kind of instance attribute reference is a method. A method is a function that “belongs to” an object. (In Python, the term method is not unique to class instances: other object types can have methods as well. For example, list objects have methods called append, insert, remove, sort, and so on.)

Valid method names of an instance object depend on its class. By definition, all attributes of a class that are function objects define corresponding methods of its instances. So in our example, `x.f` is a valid method reference, since `MyClass.f` is a function, but `x.i` is not, since `MyClass.i` is not. But `x.f` is not the same thing as `MyClass.f` — it is a method object, not a function object.

调用方法时，实例将自己作为第一个参数：`x.f()` is exactly equivalent to `MyClass.f(x)`

## Class and Instance Variables

Generally speaking, instance variables are for data unique to each instance and class variables are for attributes and methods shared by all instances of the class:

```python
class Dog:

    kind = 'canine'         # class variable shared by all instances

    def __init__(self, name):
        self.name = name    # instance variable unique to each instance

>>> d = Dog('Fido')
>>> e = Dog('Buddy')
>>> d.kind                  # shared by all dogs
'canine'
>>> e.kind                  # shared by all dogs
'canine'
>>> d.name                  # unique to d
'Fido'
>>> e.name                  # unique to e
'Buddy'
```

Shared data can have possibly surprising effects with involving mutable objects such as lists and dictionaries. For example, the tricks list in the following code should not be used as a class variable because just a single list would be shared by all `Dog` instances:

```python
class Dog:

    tricks = []             # mistaken use of a class variable

    def __init__(self, name):
        self.name = name

    def add_trick(self, trick):
        self.tricks.append(trick)

>>> d = Dog('Fido')
>>> e = Dog('Buddy')
>>> d.add_trick('roll over')
>>> e.add_trick('play dead')
>>> d.tricks                # unexpectedly shared by all dogs
['roll over', 'play dead']
```

Correct design of the class should use an instance variable instead:

```python
class Dog:

    def __init__(self, name):
        self.name = name
        self.tricks = []    # creates a new empty list for each dog

    def add_trick(self, trick):
        self.tricks.append(trick)

>>> d = Dog('Fido')
>>> e = Dog('Buddy')
>>> d.add_trick('roll over')
>>> e.add_trick('play dead')
>>> d.tricks
['roll over']
>>> e.tricks
['play dead']
```

## Random Remarks

Often, the first argument of a method is called `self`. This is nothing more than a convention: the name `self` has absolutely no special meaning to Python.

Any function object that is a class attribute defines a method for instances of that class. It is not necessary that the function definition is textually enclosed in the class definition: assigning a function object to a local variable in the class is also ok. For example:

```python
# Function defined outside the class
def f1(self, x, y):
    return min(x, x+y)

class C:
    f = f1

    def g(self):
        return 'hello world'

    h = g
```

Methods may call other methods by using method attributes of the self argument:

```python
class Bag:
    def __init__(self):
        self.data = []

    def add(self, x):
        self.data.append(x)

    def addtwice(self, x):
        self.add(x)
        self.add(x)
```

Each value is an object, and therefore has a class (also called its type). It is stored as `object.__class__`.

## Inheritance

```python
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```

when the base class is defined in another module:

```python
class DerivedClassName(modname.BaseClassName):
```

attribute references: if a requested attribute is not found in the class, the search proceeds to look in the base class. This rule is applied recursively if the base class itself is derived from some other class.

Method references are resolved as follows: the corresponding class attribute is searched, descending down the chain of base classes if necessary, and the method reference is valid if this yields a function object.

Derived classes may override methods of their base classes. Because methods have no special privileges when calling other methods of the same object, a method of a base class that calls another method defined in the same base class may end up calling a method of a derived class that overrides it. (For C++ programmers: all methods in Python are effectively virtual.)

An overriding method in a derived class may in fact want to extend rather than simply replace the base class method of the same name. There is a simple way to call the base class method directly: just call `BaseClassName.methodname(self, arguments)`.

Python has two built-in functions that work with inheritance:

- Use `isinstance()` to check an instance’s type: `isinstance(obj, int)` will be `True` only if `obj.__class__` is `int` or some class derived from `int`.
- Use `issubclass()` to check class inheritance: `issubclass(bool, int)` is `True` since `bool` is a subclass of `int`. However, `issubclass(float, int)` is `False` since `float` is not a subclass of `int`.

## Multiple Inheritance

```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```
**太多不看版**：拓扑排序，每层都是从左至右，找到就停

**这是假的**：For most purposes, in the simplest cases, you can think of the search for attributes inherited from a parent class as depth-first, left-to-right, not searching twice in the same class where there is an overlap in the hierarchy. Thus, if an attribute is not found in DerivedClassName, it is searched for in Base1, then (recursively) in the base classes of Base1, and if it was not found there, it was searched for in Base2, and so on.

**这才是真的**：In fact, it is slightly more complex than that; the method resolution order changes dynamically to support cooperative calls to super(). This approach is known in some other multiple-inheritance languages as call-next-method and is more powerful than the super call found in single-inheritance languages.

Dynamic ordering is necessary because all cases of multiple inheritance exhibit one or more diamond relationships (where at least one of the parent classes can be accessed through multiple paths from the bottommost class). For example, all classes inherit from object, so any case of multiple inheritance provides more than one path to reach object. To keep the base classes from being accessed more than once, the dynamic algorithm linearizes the search order in a way that preserves the left-to-right ordering specified in each class, that calls each parent only once, and that is monotonic (meaning that a class can be subclassed without affecting the precedence order of its parents). Taken together, these properties make it possible to design reliable and extensible classes with multiple inheritance.

## 调用父类构造函数

```python
# 调用最近的父类的构造函数
super().__init__(arg1, arg2, ... )

# 调用指定父类的构造函数
super(Child, self).__init__(arg1, arg2, ... )
Father.__init__(self, arg1, arg2, ... )
```

调用父类其他属性同构造函数

## Private Variables

“Private” instance variables that cannot be accessed except from inside an object don’t exist in Python. However, there is a convention that is followed by most Python code: a name prefixed with an underscore (e.g. `_spam`) should be treated as a non-public part of the API (whether it is a function, a method or a data member).

- 一个下划线是protected，并不会进行后面的操作

Since there is a valid use-case for class-private members (namely to avoid name clashes of names with names defined by subclasses), there is limited support for such a mechanism, called name mangling. Any identifier of the form `__spam` (at least two leading underscores, at most one trailing underscore) is textually replaced with `_classname__spam`, where classname is the current class name with leading underscore(s) stripped. This mangling is done without regard to the syntactic position of the identifier, as long as it occurs within the definition of a class.

Name mangling is helpful for letting subclasses override methods without breaking intraclass method calls. For example:

```python
class Father:
    def __init__(self, value):
        self.value = value

    def __print(self):
        print('Father', self.value)

class Child(Father):
    def __print(self):
        print('Child', self.value)

    def father_print(self):
        self._Father__print()

    def child_print(self):
        self.__print()

c = Child(10)
c.child_print()
c.father_print()
c._Child__print()
c._Father__print()
print(dir(Father))
print(dir(Child))
print(dir(c))
```

运行结果：

```python
Child 10
Father 10
Child 10
Father 10
['_Father__print', ... ]
['_Child__print', '_Father__print', ... , 'child_print', 'father_print']
['_Child__print', '_Father__print', ... , 'child_print', 'father_print', 'value']
```

上面这个例子告诉我们，其实python的私有属性就是改了名字，让原来的名字在外面访问不到。

Note that the mangling rules are designed mostly to avoid accidents; it still is possible to access or modify a variable that is considered private. This can even be useful in special circumstances, such as in the debugger.

Notice that code passed to `exec()` or `eval()` does not consider the classname of the invoking class to be the current class; this is similar to the effect of the global statement, the effect of which is likewise restricted to code that is byte-compiled together. The same restriction applies to `getattr()`, `setattr()` and `delattr()`, as well as when referencing `__dict__` directly.

## Odds and Ends

Sometimes it is useful to have a data type similar to the Pascal “record” or C “struct”, bundling together a few named data items. An empty class definition will do nicely:

```python
class Employee:
    pass

john = Employee()  # Create an empty employee record

# Fill the fields of the record
john.name = 'John Doe'
john.dept = 'computer lab'
john.salary = 1000
```

A piece of Python code that expects a particular abstract data type can often be passed a class that emulates the methods of that data type instead. For instance, if you have a function that formats some data from a file object, you can define a class with methods `read()` and `readline()` that get the data from a string buffer instead, and pass it as an argument.

Instance method objects have attributes, too: `m.__self__` is the instance object with the method `m()`, and `m.__func__` is the function object corresponding to the method.

# 装饰器

# 列表生成式

List comprehensions provide a concise way to create lists. Common applications are to make new lists where each element is the result of some operations applied to each member of another sequence or iterable, or to create a subsequence of those elements that satisfy a certain condition.

For example, assume we want to create a list of squares, like:

```python
>>>
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

Note that this creates (or overwrites) a variable named `x` that still exists after the loop completes. We can calculate the list of squares without any side effects using:

```python
squares = list(map(lambda x: x**2, range(10)))
```

or, equivalently:

```python
squares = [x**2 for x in range(10)]
```

which is more concise and readable.

A list comprehension consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. The result will be a new list resulting from evaluating the expression in the context of the for and if clauses which follow it. For example, this listcomp combines the elements of two lists if they are not equal:

```python
>>>
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

and it’s equivalent to:

```python
>>>
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

Note how the order of the for and if statements is the same in both these snippets.

If the expression is a tuple (e.g. the (x, y) in the previous example), it must be parenthesized.

```python
>>>
>>> vec = [-4, -2, 0, 2, 4]
>>> # create a new list with the values doubled
>>> [x*2 for x in vec]
[-8, -4, 0, 4, 8]
>>> # filter the list to exclude negative numbers
>>> [x for x in vec if x >= 0]
[0, 2, 4]
>>> # apply a function to all the elements
>>> [abs(x) for x in vec]
[4, 2, 0, 2, 4]
>>> # call a method on each element
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
>>> # create a list of 2-tuples like (number, square)
>>> [(x, x**2) for x in range(6)]
[(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
>>> # the tuple must be parenthesized, otherwise an error is raised
>>> [x, x**2 for x in range(6)]
  File "<stdin>", line 1, in <module>
    [x, x**2 for x in range(6)]
               ^
SyntaxError: invalid syntax
>>> # flatten a list using a listcomp with two 'for'
>>> vec = [[1,2,3], [4,5,6], [7,8,9]]
>>> [num for elem in vec for num in elem]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

List comprehensions can contain complex expressions and nested functions:

```python
>>>
>>> from math import pi
>>> [str(round(pi, i)) for i in range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

# 迭代器

## Iterators

By now you have probably noticed that most container objects can be looped over using a for statement:

```python
for element in [1, 2, 3]:
    print(element)
for element in (1, 2, 3):
    print(element)
for key in {'one':1, 'two':2}:
    print(key)
for char in "123":
    print(char)
for line in open("myfile.txt"):
    print(line, end='')
```

This style of access is clear, concise, and convenient. The use of iterators pervades and unifies Python. 

Behind the scenes, the for statement calls `iter()` on the container object. 

The function returns an `iterator` object that defines the method `__next__()` which accesses elements in the container one at a time. 

When there are no more elements, `__next__()` raises a `StopIteration` exception which tells the for loop to terminate. 

You can call the `__next__()` method using the `next()` built-in function; this example shows how it all works:

```python
>>>
>>> s = 'abc'
>>> it = iter(s)
>>> it
<iterator object at 0x00A1DB50>
>>> next(it)
'a'
>>> next(it)
'b'
>>> next(it)
'c'
>>> next(it)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    next(it)
StopIteration
```

Having seen the mechanics behind the iterator protocol, it is easy to add iterator behavior to your classes. Define an` __iter__()` method which returns an object with a `__next__()` method.

If the class defines `__next__()`, then `__iter__()` can just return self:

```python
class Reverse:
    """Iterator for looping over a sequence backwards."""
    def __init__(self, data):
        self.data = data
        self.index = len(data)

    def __iter__(self):
        return self

    def __next__(self):
        if self.index == 0:
            raise StopIteration
        self.index = self.index - 1
        return self.data[self.index]
>>>
>>> rev = Reverse('spam')
>>> iter(rev)
<__main__.Reverse object at 0x00A1DB50>
>>> for char in rev:
...     print(char)
...
m
a
p
s
```

## Iterable

ABC for classes that provide the __iter__() method.

Checking `isinstance(obj, Iterable)` detects classes that are registered as `Iterable` or that have an `__iter__()` method, but it does not detect classes that iterate with the `__getitem__()` method. The only reliable way to determine whether an object is iterable is to call `iter(obj)`.

# 生成器

## `yield` 表达式


语法：

```
yield_atom       ::=  "(" yield_expression ")"
yield_expression ::=  "yield" [expression_list | "from" expression]
```

The yield expression is used when defining a `generator` function and thus can only be used in the body of a function definition. Using a yield expression in a function’s body causes that function to be a `generator`. For example:

```python
def gen():  # defines a generator function
    yield 123
```

When a generator function is called, it returns an `iterator` known as a `generator`. That generator then controls the execution of the generator function. The execution starts when one of the generator’s methods is called. At that time, the execution proceeds to the first `yield` expression, where it is suspended again, returning the value of `expression_list` to the generator’s caller. By suspended, we mean that all local state is retained, including the current bindings of local variables, the instruction pointer, the internal evaluation stack, and the state of any exception handling. When the execution is resumed by calling one of the generator’s methods, the function can proceed exactly as if the yield expression were just another external call. 

**`yield` 表达式返回值**：The value of the yield expression after resuming depends on the method which resumed the execution. If `__next__()` is used (typically via either a for or the `next()` builtin) then the result is `None`. Otherwise, if `send()` is used, then the result will be the value passed in to that method.

**如果在 `generator` 函数结束前不再被使用**：Yield expressions are allowed anywhere in a `try` construct. If the generator is not resumed before it is finalized (by reaching a zero reference count or by being garbage collected), the generator-iterator’s `close()` method will be called, allowing any pending `finally` clauses to execute.

**`generator` 函数结束**：When the underlying iterator is complete, the `value` attribute of the raised `StopIteration` instance becomes the `value` of the `yield` expression. It can be either set explicitly when raising `StopIteration`, or automatically when the sub-iterator is a `generator` (by returning a value from the sub-generator).

The parentheses may be omitted when the `yield` expression is the sole expression on the right hand side of an assignment statement.

### Generator-iterator methods

This subsection describes the methods of a `generator` `iterator`. They can be used to control the execution of a generator function.

Note that calling any of the generator methods below when the generator is already executing raises a `ValueError` exception.

```python
generator.__next__()
```

Starts the execution of a generator function or resumes it at the last executed `yield` expression. When a generator function is resumed with a `__next__()` method, the current `yield` expression always evaluates to `None`. The execution then continues to the next `yield` expression, where the generator is suspended again, and the value of the `expression_list` is returned to `__next__()`’s caller. If the generator exits without yielding another value, a `StopIteration` exception is raised.

This method is normally called implicitly, e.g. by a `for` loop, or by the built-in `next()` function.

```python
generator.send(value)
```

Resumes the execution and “sends” a value into the generator function. The `value` argument becomes the result of the current yield expression. The `send()` method returns the next value yielded by the generator, or raises `StopIteration` if the generator exits without yielding another value. When `send()` is called to start the generator, it must be called with `None` as the argument, because there is no `yield` expression that could receive the value.

```python
generator.throw(type[, value[, traceback]])
```

Raises an exception of type `type` at the point where the generator was paused, and returns the next value yielded by the generator function. If the generator exits without yielding another value, a `StopIteration` exception is raised. If the generator function does not catch the passed-in exception, or raises a different exception, then that exception propagates to the caller.

```python
generator.close()
```

Raises a `GeneratorExit` at the point where the generator function was paused. If the generator function then exits gracefully, is already closed, or raises `GeneratorExit` (by not catching the exception), close returns to its caller. If the generator yields a value, a `RuntimeError` is raised. If the generator raises any other exception, it is propagated to the caller. `close()` does nothing if the generator has already exited due to an exception or normal exit.

### 实例

```python
>>>
>>> def echo(value=None):
...     print("Execution starts when 'next()' is called for the first time.")
...     try:
...         while True:
...             try:
...                 value = (yield value)
...             except Exception as e:
...                 value = e
...     finally:
...         print("Don't forget to clean up when 'close()' is called.")
...
>>> generator = echo(1)
>>> print(next(generator))
Execution starts when 'next()' is called for the first time.
1
>>> print(next(generator))
None
>>> print(generator.send(2))
2
>>> generator.throw(TypeError, "spam")
TypeError('spam',)
>>> generator.close()
Don't forget to clean up when 'close()' is called.
```

# 魔法函数

# 异常处理

# 拷贝
