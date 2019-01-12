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
<span id="str-index"></span>
## 索引与截取

| | |
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

## 索引与截取
- 同[字符串的索引与截取](#str-index)

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

# 函数

# 类

# 装饰器

# 迭代器

# 生成器

# 魔法函数

# 异常处理
