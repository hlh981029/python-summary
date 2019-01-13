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
| [hex(x)](http://www.runoob.com/python3/python-func-hex.html) |   将一个整数转换为一个十六进制字符串 `0xfff` |
| [oct(x)](http://www.runoob.com/python3/python-func-oct.html) |  将一个整数转换为一个八进制字符串 `0o1234567` |
| [bin(x)](http://www.runoob.com/python3/python-func-bin.html) |  将一个整数转换为一个二进制字符串 `0b1010` |


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

<table>
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

<table>
<tbody><tr>
<th style="width:5%">序号</th><th style="width:95%">函数</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-list-len.html">len(list)</a><br>列表元素个数</td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-list-max.html">max(list)</a><br>返回列表元素最大值</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-list-min.html">min(list)</a><br>返回列表元素最小值</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-list-list.html">list(seq)</a><br>将元组转换为列表</td></tr>
</tbody></table>

## 方法

<table>
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
- 值可以取任何数据类型，但键必须是`hashable`的，如字符串，数字或元组（自定义的类也是`hashable`）。创建时如果同一个键被赋值两次，后一个值会被记住.

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

<table>
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

<table>
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
**太多不看版**：拓扑排序，深度优先，从左到右，找到就停

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

```python
>>> class Father1:
...     def __init__(self):
...         print('Father1')
...         
>>> class Father2:
...     def __init__(self):
...         print('Father2')
...         
>>> class Child(Father1, Father2):
...     def __init__(self):
...         super().__init__()      # Father1
...         Father2.__init__(self)  # Father2
...         print('Child')
...         
>>> hbz = Child()
Father1
Father2
Child
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

## 闭包的概念
我们尝试从概念上去理解一下闭包。

> 在一些语言中，在函数中可以（嵌套）定义另一个函数时，如果内部的函数引用了外部的函数的变量，则可能产生闭包。闭包可以用来在一个函数与一组“私有”变量之间创建关联关系。在给定函数被多次调用的过程中，这些私有变量能够保持其持久性。
—— 维基百科)

用比较容易懂的人话说，就是当某个函数被当成对象返回时，夹带了外部变量，就形成了一个闭包。看例子。

```python
def make_printer(msg):
    def printer():
        print(msg)  # 夹带私货（外部变量）
    return printer  # 返回的是函数，带私货的函数

printer = make_printer('Foo!')
printer()
```

支持将函数当成对象使用的编程语言，一般都支持闭包。比如Python, JavaScript。

## 如何理解闭包

闭包存在有什么意义呢？为什么需要闭包？

我个人认为，闭包存在的意义就是它夹带了外部变量（私货），如果它不夹带私货，它和普通的函数就没有任何区别。同一个的函数夹带了不同的私货，就实现了不同的功能。其实你也可以这么理解，闭包和面向接口编程的概念很像，可以把闭包理解成轻量级的接口封装。

接口定义了一套对方法签名的约束规则。

```python
def tag(tag_name):
    def add_tag(content):
        return "<{0}>{1}</{0}>".format(tag_name, content)
    return add_tag

content = 'Hello'

add_tag = tag('a')
print(add_tag(content))
# <a>Hello</a>

add_tag = tag('b')
print(add_tag(content))
# <b>Hello</b>
```

在这个例子里，我们想要一个给`content`加`tag`的功能，但是具体的`tag_name`是什么样子的要根据实际需求来定，对外部调用的接口已经确定，就是`add_tag(content)`。如果按照面向接口方式实现，我们会先把`add_tag`写成接口，指定其参数和返回类型，然后分别去实现`a`和`b`的`add_tag`。

但是在闭包的概念中，`add_tag`就是一个函数，它需要`tag_name`和`content`两个参数，只不过`tag_name`这个参数是打包带走的。所以一开始时就可以告诉我怎么打包，然后带走就行。

上面的例子不太生动，其实在我们生活和工作中，闭包的概念也很常见。比如说手机拨号，你只关心电话打给谁，而不会去纠结每个品牌的手机是怎么实现的，用到了哪些模块。再比如去餐馆吃饭，你只要付钱就可以享受到服务，你并不知道那桌饭菜用了多少地沟油。这些都可以看成闭包，返回来的是一些功能或者服务（打电话，用餐），但是这些功能使用了外部变量（天线，地沟油等等）。

你也可以把一个类实例看成闭包，当你在构造这个类时，使用了不同的参数，这些参数就是闭包里的包，这个类对外提供的方法就是闭包的功能。但是类远远大于闭包，因为闭包只是一个可以执行的函数，但是类实例则有可能提供很多方法。

## 何时使用闭包

其实闭包在Python中很常见，只不过你没特别注意这就是一个闭包。比如Python中的装饰器Decorator，假如你需要写一个带参数的装饰器，那么一般都会生成闭包。

为什么？因为Python的装饰器是一个固定的函数接口形式。它要求你的装饰器函数（或装饰器类）必须接受一个函数并返回一个函数：

```python
# how to define
def wrapper(func1):  # 接受一个callable对象
    return func2  # 返回一个对象，一般为函数
    
# how to use
def target_func(args): # 目标函数
    pass

# 调用方式一，直接包裹
result = wrapper(target_func)(args)

# 调用方式二，使用@语法，等同于方式一
@wrapper
def target_func(args):
    pass

result = target_func()
```

那么如果你的装饰器如果带参数呢？那么你就需要在原来的装饰器上再包一层，用于接收这些参数。这些参数（私货）传递到内层的装饰器里后，闭包就形成了。所以说当你的装饰器需要自定义参数时，一般都会形成闭包。（类装饰器例外）

## 闭包的包到底长什么样子

其实闭包函数相对与普通函数会多出一个__closure__的属性，里面定义了一个元组用于存放所有的cell对象，每个cell对象一一保存了这个闭包中所有的外部变量。

```python
>>> def make_printer(msg1, msg2):
        def printer():
            print(msg1, msg2)
        return printer
>>> printer = make_printer('Foo', 'Bar')  # 形成闭包

>>> printer.__closure__   # 返回cell元组
(<cell at 0x03A10930: str object at 0x039DA218>, <cell at 0x03A10910: str object at 0x039DA488>)

>>> printer.__closure__[0].cell_contents  # 第一个外部变量
'Foo'
>>> printer.__closure__[1].cell_contents  # 第二个外部变量
'Bar'
```

## 怎么写一个装饰器

在早些时候 (Python Version < 2.4，2004年以前)，为一个函数添加额外功能的写法是这样的。

```python
def debug(func):
    def wrapper():
        print("[DEBUG]: enter {}()".format(func.__name__))
        return func()
    return wrapper

def say_hello():
    print("hello!")

say_hello = debug(say_hello)  # 添加功能并保持原函数名不变
```

上面的debug函数其实已经是一个装饰器了，它对原函数做了包装并返回了另外一个函数，额外添加了一些功能。因为这样写实在不太优雅，在后面版本的Python中支持了@语法糖，下面代码等同于早期的写法。

```python
def debug(func):
    def wrapper():
        print("[DEBUG]: enter {}()".format(func.__name__))
        return func()
    return wrapper

@debug
def say_hello():
    print("hello!")
```

这是最简单的装饰器，但是有一个问题，如果被装饰的函数需要传入参数，那么这个装饰器就坏了。因为返回的函数并不能接受参数，你可以指定装饰器函数`wrapper`接受和原函数一样的参数，比如：

```python
def debug(func):
    def wrapper(something):  # 指定一毛一样的参数
        print("[DEBUG]: enter {}()".format(func.__name__))
        return func(something)
    return wrapper  # 返回包装过函数

@debug
def say(something):
    print("hello {}!".format(something))
```

这样你就解决了一个问题，但又多了N个问题。因为函数有千千万，你只管你自己的函数，别人的函数参数是什么样子，鬼知道？还好Python提供了可变参数`*args`和关键字参数`**kwargs`，有了这两个参数，装饰器就可以用于任意目标函数了。

```python
def debug(func):
    def wrapper(*args, **kwargs):  # 指定宇宙无敌参数
        print("[DEBUG]: enter {}()".format(func.__name__))
        print('Prepare and say...',)
        return func(*args, **kwargs)
    return wrapper  # 返回

@debug
def say(something):
    print("hello {}!".format(something))
```

至此，你已完全掌握初级的装饰器写法。

## 带参数的装饰器

假设我们前文的装饰器需要完成的功能不仅仅是能在进入某个函数后打出log信息，而且还需指定log的级别，那么装饰器就会是这样的。

```python
def logging(level):
    def wrapper(func):
        def inner_wrapper(*args, **kwargs):
            print("[{level}]: enter function {func}()".format(
                level=level,
                func=func.__name__))
            return func(*args, **kwargs)
        return inner_wrapper
    return wrapper

@logging(level='INFO')
def say(something):
    print("say {}!".format(something))

# 如果没有使用@语法，等同于
# say = logging(level='INFO')(say)

@logging(level='DEBUG')
def do(something):
    print("do {}...".format(something))

if __name__ == '__main__':
    say('hello')
    do("my work")
```

是不是有一些晕？你可以这么理解，当带参数的装饰器被打在某个函数上时，比如`@logging(level='DEBUG')`，它其实是一个函数，会马上被执行，只要这个它返回的结果是一个装饰器时，那就没问题。细细再体会一下。

## 基于类实现的装饰器

装饰器函数其实是这样一个接口约束，它必须接受一个`callable`对象作为参数，然后返回一个`callable`对象。在Python中一般`callable`对象都是函数，但也有例外。只要某个对象重载了`__call__()`方法，那么这个对象就是`callable`的。

```python
class Test():
    def __call__(self):
        print('call me!')

t = Test()
t()  # call me
```

像`__call__`这样前后都带下划线的方法在Python中被称为内置方法，有时候也被称为魔法方法。重载这些魔法方法一般会改变对象的内部行为。上面这个例子就让一个类对象拥有了被调用的行为。

回到装饰器上的概念上来，装饰器要求接受一个`callable`对象，并返回一个`callable`对象（不太严谨，详见后文）。那么用类来实现也是也可以的。我们可以让类的构造函数`__init__()`接受一个函数，然后重载`__call__()`并返回一个函数，也可以达到装饰器函数的效果。

```python
class logging(object):
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        print("[DEBUG]: enter function {func}()".format(
            func=self.func.__name__))
        return self.func(*args, **kwargs)
@logging
def say(something):
    print("say {}!".format(something))
```

## 带参数的类装饰器

如果需要通过类形式实现带参数的装饰器，那么会比前面的例子稍微复杂一点。那么在构造函数里接受的就不是一个函数，而是传入的参数。通过类把这些参数保存起来。然后在重载`__call__`方法是就需要接受一个函数并返回一个函数。

```python
class logging(object):
    def __init__(self, level='INFO'):
        self.level = level
        
    def __call__(self, func): # 接受函数
        def wrapper(*args, **kwargs):
            print("[{level}]: enter function {func}()".format(
                level=self.level,
                func=func.__name__))
            func(*args, **kwargs)
        return wrapper  #返回函数

@logging(level='INFO')
def say(something):
    print("say {}!".format(something))
```

## 装饰器里的那些坑

装饰器可以让你代码更加优雅，减少重复，但也不全是优点，也会带来一些问题。

### 位置错误的代码

让我们直接看示例代码。

```python
def html_tags(tag_name):
    print('begin outer function.')
    def wrapper_(func):
        print("begin of inner wrapper function.")
        def wrapper(*args, **kwargs):
            content = func(*args, **kwargs)
            print("<{tag}>{content}</{tag}>".format(tag=tag_name, content=content))
        print('end of inner wrapper function.')
        return wrapper
    print('end of outer function')
    return wrapper_

@html_tags('b')
def hello(name='Toby'):
    return 'Hello {}!'.format(name)

hello()
hello()
```

在装饰器中我在各个可能的位置都加上了`print`语句，用于记录被调用的情况。你知道他们最后打印出来的顺序吗？如果你心里没底，那么最好不要在装饰器函数之外添加逻辑功能，否则这个装饰器就不受你控制了。以下是输出结果：

```python
begin outer function.
end of outer function
begin of inner wrapper function.
end of inner wrapper function.
<b>Hello Toby!</b>
<b>Hello Toby!</b>
```

### 多层装饰器

```python
# an example of python decorator
def deco1(func):
    print(1)
    def wrapper1():
        print(2)
        func()
        print(3)
    print(4)
    return wrapper1

def deco2(func):
    print(5)
    def wrapper2():
        print(6)
        func()
        print(7)
    print(8)
    return wrapper2

@deco1
@deco2
def foo():
    print('foo')


if __name__ == '__main__':
    foo()
```

运行结果：

```
5
8
1
4
2
6
foo
7
3
```

修饰器本质上就是一个函数，只不过它的传入参数同样是一个函数。因此，依次加了`deco1`和`deco2`两个装饰器的原函数`foo`实际上相当于`deco1(deco2(foo))`。

明白了第1步后，下面进入这个复合函数。首先执行的是内层函数`deco2(foo)`。因此第一个打印值是`5`。接下来要注意，在`deco2`这个函数内定义了一个`wrapper2`函数，但是并没有类似于`wrapper2()`的语句，因此该函数内的语句并没有立即执行，而是作为了返回值。因此`wrapper2`内的3条语句作为输入参数传递到了`deco1`内。`wrapper2`函数内还有一行`print(8)`，因此第二个打印值为`8`。

下一步是执行`deco1()`函数内容。与2类似，先打印出`1`和`4`，返回值为`wrapper1`。由于更外层没有装饰器，因此接下来就将执行`wrapper1`内的内容。第五个打印值为`2`。接着执行`func()`函数，注意此处`func()`表示的是`wrapper2`中的内容，因此跳到`wrapper2`中执行。第六个打印值为`6`。类似的，`wrapper2`中的`func()`为`foo()`，因此接着会输出`foo`。最后，回到wrapper2和`wrapper1`的最后一行，依次输出`7`和`3`。到这里，整个装饰器的运行过程结束。

### 错误的函数签名和文档

装饰器装饰过的函数看上去名字没变，其实已经变了。

```python
def logging(func):
    def wrapper(*args, **kwargs):
        """print log before a function."""
        print("[DEBUG] {}: enter {}()".format(datetime.now(), func.__name__))
        return func(*args, **kwargs)
    return wrapper

@logging
def say(something):
    """say something"""
    print("say {}!".format(something))

print(say.__name__)  # wrapper
```

为什么会这样呢？只要你想想装饰器的语法糖@代替的东西就明白了。@等同于这样的写法。

```python
say = logging(say)
```

`logging`其实返回的函数名字刚好是`wrapper`，那么上面的这个语句刚好就是把这个结果赋值给`say`，`say`的`__name__`自然也就是`wrapper`了，不仅仅是`name`，其他属性也都是来自`wrapper`，比如`doc`，`source`等等。

使用标准库里的`functools.wraps`，可以基本解决这个问题。

```python
from functools import wraps

def logging(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        """print log before a function."""
        print("[DEBUG] {}: enter {}()".format(datetime.now(), func.__name__))
        return func(*args, **kwargs)
    return wrapper

@logging
def say(something):
    """say something"""
    print("say {}!".format(something))

print(say.__name__)  # say
print(say.__doc__) # say something
```

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

**`yield` 表达式返回值**：The value of the yield expression after resuming depends on the method which resumed the execution. If `__next__()` is used (typically via either a for or the `next()` builtin) then the result is `None`. Otherwise, if `send()` is used, then the result will be the value passed in to that method.

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

## `yield form`

PEP 380 adds the `yield from` expression, allowing a generator to delegate part of its operations to another generator. This allows a section of code containing `yield` to be factored out and placed in another generator. Additionally, the subgenerator is allowed to return with a value, and the value is made available to the delegating generator.

While designed primarily for use in delegating to a subgenerator, the `yield from` expression actually allows delegation to arbitrary subiterators.

For simple iterators, yield from iterable is essentially just a shortened form of `for item in iterable: yield item:`

```python
>>>
>>> def g(x):
...     yield from range(x, 0, -1)
...     yield from range(x)
...
>>> list(g(5))
[5, 4, 3, 2, 1, 0, 1, 2, 3, 4]
```

However, unlike an ordinary loop, `yield from` allows subgenerators to receive sent and thrown values directly from the calling scope, and return a final value to the outer generator:

```python
>>>
>>> def accumulate():
...     tally = 0
...     while 1:
...         next = yield
...         if next is None:
...             return tally
...         tally += next
...
>>> def gather_tallies(tallies):
...     while 1:
...         tally = yield from accumulate()
...         tallies.append(tally)
...
>>> tallies = []
>>> acc = gather_tallies(tallies)
>>> next(acc)  # Ensure the accumulator is ready to accept values
>>> for i in range(4):
...     acc.send(i)
...
>>> acc.send(None)  # Finish the first tally
>>> for i in range(5):
...     acc.send(i)
...
>>> acc.send(None)  # Finish the second tally
>>> tallies
[6, 10]
```

The main principle driving this change is to allow even generators that are designed to be used with the send and throw methods to be split into multiple subgenerators as easily as a single large function can be split into multiple subfunctions.

# 属性

```python
class property(fget=None, fset=None, fdel=None, doc=None)
```

Return a property attribute.

`fget` is a function for getting an attribute value. `fset` is a function for setting an attribute value. `fdel` is a function for deleting an attribute value. And `doc` creates a docstring for the attribute.

A typical use is to define a managed attribute `x`:

```python
class C:
    def __init__(self):
        self._x = None

    def getx(self):
        return self._x

    def setx(self, value):
        self._x = value

    def delx(self):
        del self._x

    x = property(getx, setx, delx, "I'm the 'x' property.")
```

If `c` is an instance of `C`, `c.x` will invoke the getter, `c.x = value` will invoke the setter and `del c.x` the deleter.

If given, `doc` will be the docstring of the property attribute. Otherwise, the property will copy `fget`’s docstring (if it exists). This makes it possible to create read-only properties easily using `property()` as a decorator:

```python
class Parrot:
    def __init__(self):
        self._voltage = 100000

    @property
    def voltage(self):
        """Get the current voltage."""
        return self._voltage
```

The `@property` decorator turns the `voltage()` method into a “getter” for a read-only attribute with the same name, and it sets the docstring for `voltage` to `“Get the current voltage.”`

A property object has `getter`, `setter`, and `deleter` methods usable as decorators that create a copy of the property with the corresponding accessor function set to the decorated function. This is best explained with an example:

```python
class C:
    def __init__(self):
        self._x = None

    @property
    def x(self):
        """I'm the 'x' property."""
        return self._x

    @x.setter
    def x(self, value):
        self._x = value

    @x.deleter
    def x(self):
        del self._x
```

This code is exactly equivalent to the first example. Be sure to give the additional functions the same name as the original property (`x` in this case.)

The returned property object also has the attributes `fget`, `fset`, and `fdel` corresponding to the constructor arguments.

# 只读（两种方法）

## 通过私有属性

用私有属性+@property定义只读属性, 需要预先定义好属性名, 然后实现对应的getter方法.

```python
class Vector2D(object):
    def __init__(self, x, y):
        self.__x = float(x)
        self.__y = float(y)

    @property
    def x(self):
        return self.__x
    @property
    def y(self):
        return self.__y

if __name__ == "__main__":
    v = Vector2D(3, 4)
    print(v.x, v.y)
    v.x = 8 # error will be raised.
```

输出:

```python
(3.0, 4.0)
Traceback (most recent call last):
  File ...., line 16, in <module>
    v.x = 8 # error will be raised.
AttributeError: can't set attribute
```

可以看出, 属性x是可读但不可写的.

## 通过__setattr__

当我们调用obj.attr=value时发生了什么?

很简单, 调用了obj的__setattr__方法. 可通过以下代码验证:

```python
class MyCls():
    def __init__(self):
        pass

    def __setattr__(self, f, v):
        print 'setting %r = %r'%(f, v)
if __name__ == '__main__':
    obj = MyCls()
    obj.new_field = 1
```

输出:

```python
setting 'new_field' = 1
1
```

所以呢, 只需要在__setattr__ 方法里挡一下, 就可以阻止属性值的设置, 可谓是釜底抽薪. 代码:

```python
class MyCls(object):
    def __init__(self):
        self.__readonly_property = 'readonly_property'

    def __getattr__(self, item):
        if item == 'readonly_property':
            return self.__readonly_property

    def __setattr__(self, f, v):
        if f == 'readonly_property':
            raise AttributeError(f'{type(self).__name__}.{f} is READ ONLY')
        else:
            self.__dict__[f] = v

if __name__ == '__main__':
    obj = MyCls()
    obj.any_other_property = 'any_other_property'
    print(obj.any_other_property)
    print(obj.readonly_property)
    obj.readonly_property = 1
```

输出:

```python
any_other_property
readonly_property
Traceback (most recent call last):
  File "...", line 20, in <module>
    obj.readonly_property = 1
    ...
  AttributeError: MyCls.readonly_property is READ ONLY
```

# 方法

## 类方法

```python
@classmethod
```

Transform a method into a class method.

A class method receives the class as implicit first argument, just like an instance method receives the instance. To declare a class method, use this idiom:

```python
class C:
    @classmethod
    def f(cls, arg1, arg2, ...): ...
```

The `@classmethod` form is a function decorator.

It can be called either on the class (such as `C.f()`) or on an instance (such as `C().f()`). The instance is ignored except for its class. If a class method is called for a derived class, the derived class object is passed as the implied first argument.

## 静态方法

```python
@staticmethod
```

Transform a method into a static method.

A static method does not receive an implicit first argument. To declare a static method, use this idiom:

```python
class C:
    @staticmethod
    def f(arg1, arg2, ...): ...
```

The `@staticmethod` form is a function decorator.

It can be called either on the class (such as `C.f()`) or on an instance (such as `C().f()`). The instance is ignored except for its class.

Like all decorators, it is also possible to call staticmethod as a regular function and do something with its result. This is needed in some cases where you need a reference to a function from a class body and you want to avoid the automatic transformation to instance method. For these cases, use this idiom:

```python
class C:
    builtin_open = staticmethod(open)
```

## 虚方法

```python
@abc.abstractmethod
```

A decorator indicating abstract methods.

Using this decorator requires that the class’s metaclass is `ABCMeta` or is derived from it. A class that has a metaclass derived from `ABCMeta` cannot be instantiated unless all of its abstract methods and properties are overridden. The abstract methods can be called using any of the normal ‘super’ call mechanisms. `abstractmethod()` may be used to declare abstract methods for properties and descriptors.

Dynamically adding abstract methods to a class, or attempting to modify the abstraction status of a method or class once it is created, are not supported.

When `abstractmethod()` is applied in combination with other method descriptors, it should be applied as the innermost decorator, as shown in the following usage examples:

```python
class C(ABC):
    @abstractmethod
    def my_abstract_method(self, ...):
        ...
    @classmethod
    @abstractmethod
    def my_abstract_classmethod(cls, ...):
        ...
    @staticmethod
    @abstractmethod
    def my_abstract_staticmethod(...):
        ...

    @property
    @abstractmethod
    def my_abstract_property(self):
        ...
    @my_abstract_property.setter
    @abstractmethod
    def my_abstract_property(self, val):
        ...

    @abstractmethod
    def _get_x(self):
        ...
    @abstractmethod
    def _set_x(self, val):
        ...
    x = property(_get_x, _set_x)
```

In order to correctly interoperate with the abstract base class machinery, the descriptor must identify itself as abstract using `__isabstractmethod__`. In general, this attribute should be `True` if any of the methods used to compose the descriptor are abstract. For example, Python’s built-in property does the equivalent of:

```python
class Descriptor:
    ...
    @property
    def __isabstractmethod__(self):
        return any(getattr(f, '__isabstractmethod__', False) for
                   f in (self._fget, self._fset, self._fdel))
```

Note Unlike Java abstract methods, these abstract methods may have an implementation. This implementation can be called via the `super()` mechanism from the class that overrides it. This could be useful as an end-point for a super-call in a framework that uses cooperative multiple-inheritance.

# 魔法函数

A class can implement certain operations that are invoked by special syntax (such as arithmetic operations or subscripting and slicing) by defining methods with special names. This is Python’s approach to operator overloading, allowing classes to define their own behavior with respect to language operators. For instance, if a class defines a method named `__getitem__()`, and `x` is an instance of this class, then `x[i]` is roughly equivalent to `type(x).__getitem__(x, i)`. Except where mentioned, attempts to execute an operation raise an exception when no appropriate method is defined (typically `AttributeError` or `TypeError`).

Setting a special method to `None` indicates that the corresponding operation is not available. For example, if a class sets `__iter__()` to `None`, the class is not iterable, so calling `iter()` on its instances will raise a `TypeError` (without falling back to `__getitem__()`).

## Basic customization

```python
object.__new__(cls[, ...])
```

Called to create a new instance of class `cls. __new__()` is a static method (special-cased so you need not declare it as such) that takes the class of which an instance was requested as its first argument. The remaining arguments are those passed to the object constructor expression (the call to the class). The return value of `__new__()` should be the new object instance (usually an instance of `cls`).

Typical implementations create a new instance of the class by invoking the superclass’s `__new__()` method using `super().__new__(cls[, ...])` with appropriate arguments and then modifying the newly-created instance as necessary before returning it.

If `__new__()` returns an instance of `cls`, then the new instance’s `__init__()` method will be invoked like `__init__(self[, ...])`, where self is the new instance and the remaining arguments are the same as were passed to `__new__()`.

If `__new__()` does not return an instance of `cls`, then the new instance’s `__init__()` method will not be invoked.

`__new__()` is intended mainly to allow subclasses of immutable types (like `int`, `str`, or `tuple`) to customize instance creation. It is also commonly overridden in custom metaclasses in order to customize class creation.

```python
object.__init__(self[, ...])
```

Called after the instance has been created (by `__new__()`), but before it is returned to the caller. The arguments are those passed to the class constructor expression. If a base class has an `__init__()` method, the derived class’s `__init__()` method, if any, must explicitly call it to ensure proper initialization of the base class part of the instance; for example: `super().__init__([args...])`.

Because `__new__()` and `__init__()` work together in constructing objects (`__new__()` to create it, and `__init__()` to customize it), no non-None value may be returned by `__init__()`; doing so will cause a `TypeError` to be raised at runtime.

```python
object.__del__(self)
```

Called when the instance is about to be destroyed. This is also called a finalizer or (improperly) a destructor. If a base class has a `__del__()` method, the derived class’s `__del__()` method, if any, must explicitly call it to ensure proper deletion of the base class part of the instance.

```python
object.__repr__(self)
```

Called by the `repr()` built-in function to compute the “official” string representation of an object. If at all possible, this should look like a valid Python expression that could be used to recreate an object with the same value (given an appropriate environment). If this is not possible, a string of the form `<...some useful description...>` should be returned. The return value must be a string object. If a class defines `__repr__()` but not `__str__()`, then `__repr__()` is also used when an “informal” string representation of instances of that class is required.

This is typically used for debugging, so it is important that the representation is information-rich and unambiguous.

```python
object.__str__(self)
```

Called by `str(object)` and the built-in functions `format()` and `print()` to compute the “informal” or nicely printable string representation of an object. The return value must be a string object.

This method differs from `object.__repr__()` in that there is no expectation that `__str__()` return a valid Python expression: a more convenient or concise representation can be used.

The default implementation defined by the built-in type object calls `object.__repr__()`.

```python
object.__bytes__(self)
```

Called by bytes to compute a byte-string representation of an object. This should return a bytes object.

```python
object.__lt__(self, other)
object.__le__(self, other)
object.__eq__(self, other)
object.__ne__(self, other)
object.__gt__(self, other)
object.__ge__(self, other)
```

These are the so-called “rich comparison” methods. The correspondence between operator symbols and method names is as follows:
- `x<y` calls `x.__lt__(y)`
- `x<=y` calls `x.__le__(y)`
- `x==y` calls `x.__eq__(y)`
- `x!=y` calls `x.__ne__(y)`
- `x>y` calls `x.__gt__(y)`
- `x>=y` calls `x.__ge__(y)`

A rich comparison method may return the singleton `NotImplemented` if it does not implement the operation for a given pair of arguments. By convention, `False` and `True` are returned for a successful comparison. However, these methods can return any value, so if the comparison operator is used in a Boolean context (e.g., in the condition of an if statement), Python will call `bool()` on the value to determine if the result is true or false.

By default, `__ne__()` delegates to `__eq__()` and inverts the result unless it is `NotImplemented`. There are no other implied relationships among the comparison operators, for example, the truth of (`x<y or x==y`) does not imply `x<=y`.

```python
object.__hash__(self)
```

Called by built-in function `hash()` and for operations on members of hashed collections including `set`, `frozenset`, and `dict`. `__hash__()` should return an integer. The only required property is that objects which compare equal have the same hash value; it is advised to mix together the hash values of the components of the object that also play a part in comparison of objects by packing them into a tuple and hashing the tuple. Example:

```python
def __hash__(self):
    return hash((self.name, self.nick, self.color))
```

If a class does not define an `__eq__()` method it should not define a `__hash__()` operation either; if it defines `__eq__()` but not `__hash__()`, its instances will not be usable as items in hashable collections. If a class defines mutable objects and implements an `__eq__()` method, it should not implement `__hash__()`, since the implementation of hashable collections requires that a key’s hash value is immutable (if the object’s hash value changes, it will be in the wrong hash bucket).

User-defined classes have `__eq__()` and `__hash__()` methods by default; with them, all objects compare unequal (except with themselves) and `x.__hash__()` returns an appropriate value such that `x == y` implies both that x is y and hash(x) == hash(y).

A class that overrides `__eq__()` and does not define `__hash__()` will have its `__hash__()` implicitly set to `None`. When the `__hash__()` method of a class is `None`, instances of the class will raise an appropriate `TypeError` when a program attempts to retrieve their hash value, and will also be correctly identified as unhashable when checking `isinstance(obj, collections.abc.Hashable)`.

```python
object.__bool__(self)
```

Called to implement truth value testing and the built-in operation `bool()`; should return `False` or `True`. When this method is not defined, `__len__()` is called, if it is defined, and the object is considered true if its result is nonzero. If a class defines neither `__len__()` nor `__bool__()`, all its instances are considered true.

## Customizing attribute access

The following methods can be defined to customize the meaning of attribute access (use of, assignment to, or deletion of x.name) for class instances.

```python
object.__getattr__(self, name)
```

Called when the default attribute access fails with an `AttributeError` (either `__getattribute__()` raises an `AttributeError` because name is not an instance attribute or an attribute in the class tree for self; or `__get__()` of a name property raises `AttributeError`). This method should either return the (computed) attribute value or raise an `AttributeError` exception.

Note that if the attribute is found through the normal mechanism, `__getattr__()` is not called. (This is an intentional asymmetry between `__getattr__()` and `__setattr__()`.) This is done both for efficiency reasons and because otherwise `__getattr__()` would have no way to access other attributes of the instance. Note that at least for instance variables, you can fake total control by not inserting any values in the instance attribute dictionary (but instead inserting them in another object). See the __getattribute__() method below for a way to actually get total control over attribute access.

```python
object.__getattribute__(self, name)
```

Called unconditionally to implement attribute accesses for instances of the class. If the class also defines `__getattr__()`, the latter will not be called unless `__getattribute__()` either calls it explicitly or raises an `AttributeError`. This method should return the (computed) attribute value or raise an `AttributeError` exception. In order to avoid infinite recursion in this method, its implementation should always call the base class method with the same name to access any attributes it needs, for example, `object.__getattribute__(self, name)`.

```python
object.__setattr__(self, name, value)
```

Called when an attribute assignment is attempted. This is called instead of the normal mechanism (i.e. store the value in the instance dictionary). name is the attribute name, value is the value to be assigned to it.

If `__setattr__()` wants to assign to an instance attribute, it should call the base class method with the same name, for example, `object.__setattr__(self, name, value)`.

```python
object.__delattr__(self, name)
```

Like `__setattr__()` but for attribute deletion instead of assignment. This should only be implemented if `del obj.name` is meaningful for the object.

```python
object.__dir__(self)
```

Called when `dir()` is called on the object. A sequence must be returned. `dir()` converts the returned sequence to a list and sorts it.

### Customizing module attribute access

Special names `__getattr__` and `__dir__` can be also used to customize access to module attributes. The `__getattr__` function at the module level should accept one argument which is the name of an attribute and return the computed value or raise an `AttributeError`. If an attribute is not found on a module object through the normal lookup, i.e. `object.__getattribute__()`, then `__getattr__` is searched in the module `__dict__` before raising an `AttributeError`. If found, it is called with the attribute name and the result is returned.

The `__dir__` function should accept no arguments, and return a list of strings that represents the names accessible on module. If present, this function overrides the standard `dir()` search on a module.

### `__slots__`

`__slots__` allow us to explicitly declare data members (like properties) and deny the creation of `__dict__` and `__weakref__` (unless explicitly declared in `__slots__` or available in a parent.)

The space saved over using `__dict__` can be significant.

```python
object.__slots__
```

This class variable can be assigned a string, iterable, or sequence of strings with variable names used by instances. `__slots__` reserves space for the declared variables and prevents the automatic creation of `__dict__` and `__weakref__` for each instance.

- When inheriting from a class without `__slots__`, the `__dict__` and `__weakref__` attribute of the instances will always be accessible.
- Without a `__dict__` variable, instances cannot be assigned new variables not listed in the `__slots__` definition. Attempts to assign to an unlisted variable name raises `AttributeError`. If dynamic assignment of new variables is desired, then add '`__dict__`' to the sequence of strings in the `__slots__` declaration.
- `__slots__` are implemented at the class level by creating descriptors (Implementing Descriptors) for each variable name. As a result, class attributes cannot be used to set default values for instance variables defined by `__slots__`; otherwise, the class attribute would overwrite the descriptor assignment.
- The action of a `__slots__` declaration is not limited to the class where it is defined. `__slots__` declared in parents are available in child classes. However, child subclasses will get a `__dict__` and `__weakref__` unless they also define `__slots__` (which should only contain names of any additional slots).
- If a class defines a slot also defined in a base class, the instance variable defined by the base class slot is inaccessible (except by retrieving its descriptor directly from the base class).
- Any non-string iterable may be assigned to `__slots__`. Mappings may also be used; however, in the future, special meaning may be assigned to the values corresponding to each key.
- Multiple inheritance with multiple slotted parent classes can be used, but only one parent is allowed to have attributes created by slots (the other bases must have empty slot layouts) - violations raise `TypeError`.

## Emulating callable objects

```python
object.__call__(self[, args...])
```

Called when the instance is “called” as a function; if this method is defined, `x(arg1, arg2, ...)` is a shorthand for `x.__call__(arg1, arg2, ...)`.

## Emulating container types

The following methods can be defined to implement container objects. Containers usually are sequences (such as lists or tuples) or mappings (like dictionaries), but can represent other containers as well. The first set of methods is used either to emulate a sequence or to emulate a mapping; the difference is that for a sequence, the allowable keys should be the integers k for which 0 <= k < N where N is the length of the sequence, or slice objects, which define a range of items. 

It is also recommended that mappings provide the methods `keys()`, `values()`, `items()`, `get()`, `clear()`, `setdefault()`, `pop()`, `popitem()`, `copy()`, and `update()` behaving similar to those for Python’s standard dictionary objects. 

Mutable sequences should provide methods `append(), count(), index(), extend(), insert(), pop(), remove(), reverse() and sort()`, like Python standard list objects.

Finally, sequence types should implement addition (meaning concatenation) and multiplication (meaning repetition) by defining the methods `__add__(), __radd__(), __iadd__(), __mul__(), __rmul__() and __imul__()` described below; they should not define other numerical operators.

It is recommended that both mappings and sequences implement the `__contains__()` method to allow efficient use of the in operator; for mappings, in should search the mapping’s keys; for sequences, it should search through the values.

It is further recommended that both mappings and sequences implement the `__iter__()` method to allow efficient iteration through the container; for mappings, `__iter__()` should be the same as `keys()`; for sequences, it should iterate through the values.

```python
object.__len__(self)
```

Called to implement the built-in function `len()`. Should return the length of the object, an integer >= 0. Also, an object that doesn’t define a `__bool__()` method and whose `__len__()` method returns zero is considered to be false in a Boolean context.

Note Slicing is done exclusively with the following three methods. A call like

```python
a[1:2] = b
```

is translated to

```python
a[slice(1, 2, None)] = b
```

and so forth. Missing slice items are always filled in with None.

```python
object.__getitem__(self, key)
```

Called to implement evaluation of `self[key]`. For sequence types, the accepted keys should be integers and slice objects. Note that the special interpretation of negative indexes (if the class wishes to emulate a sequence type) is up to the `__getitem__()` method.

```python
object.__setitem__(self, key, value)
```

Called to implement assignment to `self[key]`.

```python
object.__delitem__(self, key)
```

Called to implement deletion of `self[key]`.

```python
object.__iter__(self)
```

This method is called when an iterator is required for a container. This method should return a new iterator object that can iterate over all the objects in the container.

Iterator objects also need to implement this method; they are required to return themselves.

```python
object.__reversed__(self)
```

Called (if present) by the `reversed()` built-in to implement reverse iteration. It should return a new iterator object that iterates over all the objects in the container in reverse order.

If the `__reversed__()` method is not provided, the `reversed()` built-in will fall back to using the sequence protocol (`__len__() and __getitem__()`).

The membership test operators (`in` and `not in`) are normally implemented as an iteration through a sequence. However, container objects can supply the following special method with a more efficient implementation, which also does not require the object be a sequence.

```python
object.__contains__(self, item)
```

Called to implement membership test operators. Should return true if item is in self, false otherwise.

For objects that don’t define `__contains__()`, the membership test first tries iteration via `__iter__()`, then the old sequence iteration protocol via `__getitem__()`.

## Emulating numeric types

The following methods can be defined to emulate numeric objects. Methods corresponding to operations that are not supported by the particular kind of number implemented (e.g., bitwise operations for non-integral numbers) should be left undefined.

```python
object.__add__(self, other)
object.__sub__(self, other)
object.__mul__(self, other)
object.__matmul__(self, other)
object.__truediv__(self, other)
object.__floordiv__(self, other)
object.__mod__(self, other)
object.__divmod__(self, other)
object.__pow__(self, other[, modulo])
object.__lshift__(self, other)
object.__rshift__(self, other)
object.__and__(self, other)
object.__xor__(self, other)
object.__or__(self, other)
```

```
These methods are called to implement the binary arithmetic operations (+, -, *, @, /, //, %, divmod(), pow(), **, <<, >>, &, ^, |). For instance, to evaluate the expression x + y, where x is an instance of a class that has an __add__() method, x.__add__(y) is called. The __divmod__() method should be the equivalent to using __floordiv__() and __mod__(); it should not be related to __truediv__(). Note that __pow__() should be defined to accept an optional third argument if the ternary version of the built-in pow() function is to be supported.
```

If one of those methods does not support the operation with the supplied arguments, it should return `NotImplemented`.

```python
object.__radd__(self, other)
object.__rsub__(self, other)
object.__rmul__(self, other)
object.__rmatmul__(self, other)
object.__rtruediv__(self, other)
object.__rfloordiv__(self, other)
object.__rmod__(self, other)
object.__rdivmod__(self, other)
object.__rpow__(self, other)
object.__rlshift__(self, other)
object.__rrshift__(self, other)
object.__rand__(self, other)
object.__rxor__(self, other)
object.__ror__(self, other)
```

```
These methods are called to implement the binary arithmetic operations (+, -, *, @, /, //, %, divmod(), pow(), **, <<, >>, &, ^, |) with reflected (swapped) operands. These functions are only called if the left operand does not support the corresponding operation and the operands are of different types. For instance, to evaluate the expression x - y, where y is an instance of a class that has an __rsub__() method, y.__rsub__(x) is called if x.__sub__(y) returns NotImplemented.
```

Note that ternary pow() will not try calling `__rpow__()` (the coercion rules would become too complicated).

Note If the right operand’s type is a subclass of the left operand’s type and that subclass provides the reflected method for the operation, this method will be called before the left operand’s non-reflected method. This behavior allows subclasses to override their ancestors’ operations.

```python
object.__iadd__(self, other)
object.__isub__(self, other)
object.__imul__(self, other)
object.__imatmul__(self, other)
object.__itruediv__(self, other)
object.__ifloordiv__(self, other)
object.__imod__(self, other)
object.__ipow__(self, other[, modulo])
object.__ilshift__(self, other)
object.__irshift__(self, other)
object.__iand__(self, other)
object.__ixor__(self, other)
object.__ior__(self, other)
```

```
These methods are called to implement the augmented arithmetic assignments (+=, -=, *=, @=, /=, //=, %=, **=, <<=, >>=, &=, ^=, |=). These methods should attempt to do the operation in-place (modifying self) and return the result (which could be, but does not have to be, self). If a specific method is not defined, the augmented assignment falls back to the normal methods. For instance, if x is an instance of a class with an __iadd__() method, x += y is equivalent to x = x.__iadd__(y) . Otherwise, x.__add__(y) and y.__radd__(x) are considered, as with the evaluation of x + y..
```

```python
object.__neg__(self)
object.__pos__(self)
object.__abs__(self)
object.__invert__(self)
```

Called to implement the unary arithmetic operations (`-, +, abs() and ~`).

```python
object.__complex__(self)
object.__int__(self)
object.__float__(self)
```

Called to implement the built-in functions `complex(), int() and float()`. Should return a value of the appropriate type.

```python
object.__index__(self)
```

Called to implement `operator.index()`, and whenever Python needs to losslessly convert the numeric object to an integer object (such as in slicing, or in the built-in `bin(), hex() and oct()` functions). Presence of this method indicates that the numeric object is an integer type. Must return an integer.

Note In order to have a coherent integer type class, when `__index__()` is defined `__int__()` should also be defined, and both should return the same value.

```python
object.__round__(self[, ndigits])
object.__trunc__(self)
object.__floor__(self)
object.__ceil__(self)
```

Called to implement the built-in function `round()` and math functions `trunc(), floor() and ceil()`. Unless ndigits is passed to `__round__()` all these methods should return the value of the object truncated to an Integral (typically an int).

If `__int__()` is not defined then the built-in function int() falls back to `__trunc__()`.

### With Statement Context Managers

A context manager is an object that defines the runtime context to be established when executing a with statement. The context manager handles the entry into, and the exit from, the desired runtime context for the execution of the block of code. Context managers are normally invoked using the with statement (described in section The with statement), but can also be used by directly invoking their methods.

Typical uses of context managers include saving and restoring various kinds of global state, locking and unlocking resources, closing opened files, etc.

```python
object.__enter__(self)
```

Enter the runtime context related to this object. The with statement will bind this method’s return value to the target(s) specified in the as clause of the statement, if any.

```python
object.__exit__(self, exc_type, exc_value, traceback)
```

Exit the runtime context related to this object. The parameters describe the exception that caused the context to be exited. If the context was exited without an exception, all three arguments will be None.

If an exception is supplied, and the method wishes to suppress the exception (i.e., prevent it from being propagated), it should return a true value. Otherwise, the exception will be processed normally upon exit from this method.

Note that `__exit__()` methods should not reraise the passed-in exception; this is the caller’s responsibility.



### Special method lookup

For custom classes, implicit invocations of special methods are only guaranteed to work correctly if defined on an object’s type, not in the object’s instance dictionary. That behaviour is the reason why the following code raises an exception:

```python
>>>
>>> class C:
...     pass
...
>>> c = C()
>>> c.__len__ = lambda: 5
>>> len(c)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: object of type 'C' has no len()
```

The rationale behind this behaviour lies with a number of special methods such as `__hash__()` and `__repr__()` that are implemented by all objects, including type objects. If the implicit lookup of these methods used the conventional lookup process, they would fail when invoked on the type object itself:

```python
>>>
>>> 1 .__hash__() == hash(1)
True
>>> int.__hash__() == hash(int)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: descriptor '__hash__' of 'int' object needs an argument
```

Incorrectly attempting to invoke an unbound method of a class in this way is sometimes referred to as ‘metaclass confusion’, and is avoided by bypassing the instance when looking up special methods:

```python
>>>
>>> type(1).__hash__(1) == hash(1)
True
>>> type(int).__hash__(int) == hash(int)
True
```

In addition to bypassing any instance attributes in the interest of correctness, implicit special method lookup generally also bypasses the `__getattribute__()` method even of the object’s metaclass:

```python
>>>
>>> class Meta(type):
...     def __getattribute__(*args):
...         print("Metaclass getattribute invoked")
...         return type.__getattribute__(*args)
...
>>> class C(object, metaclass=Meta):
...     def __len__(self):
...         return 10
...     def __getattribute__(*args):
...         print("Class getattribute invoked")
...         return object.__getattribute__(*args)
...
>>> c = C()
>>> c.__len__()                 # Explicit lookup via instance
Class getattribute invoked
10
>>> type(c).__len__(c)          # Explicit lookup via type
Metaclass getattribute invoked
10
>>> len(c)                      # Implicit lookup
10
```

Bypassing the `__getattribute__()` machinery in this fashion provides significant scope for speed optimisations within the interpreter, at the cost of some flexibility in the handling of special methods (the special method must be set on the class object itself in order to be consistently invoked by the interpreter).

# 元类

## type()

动态语言和静态语言最大的不同，就是函数和类的定义，不是编译时定义的，而是运行时动态创建的。

比方说我们要定义一个Hello的class，就写一个hello.py模块：

```python
class Hello(object):
    def hello(self, name='world'):
        print('Hello, %s.' % name)
```

当Python解释器载入hello模块时，就会依次执行该模块的所有语句，执行结果就是动态创建出一个Hello的class对象，测试如下：

```python
>>> from hello import Hello
>>> h = Hello()
>>> h.hello()
Hello, world.
>>> print(type(Hello))
<class 'type'>
>>> print(type(h))
<class 'hello.Hello'>
```

type()函数可以查看一个类型或变量的类型，Hello是一个class，它的类型就是type，而h是一个实例，它的类型就是class Hello。

我们说class的定义是运行时动态创建的，而创建class的方法就是使用type()函数。

type()函数既可以返回一个对象的类型，又可以创建出新的类型，比如，我们可以通过type()函数创建出Hello类，而无需通过class Hello(object)...的定义：

```python
>>> def fn(self, name='world'): # 先定义函数
...     print('Hello, %s.' % name)
...
>>> Hello = type('Hello', (object,), dict(hello=fn)) # 创建Hello class
>>> h = Hello()
>>> h.hello()
Hello, world.
>>> print(type(Hello))
<class 'type'>
>>> print(type(h))
<class '__main__.Hello'>
```

要创建一个class对象，type()函数依次传入3个参数：

- class的名称；
- 继承的父类集合，注意Python支持多重继承，如果只有一个父类，别忘了tuple的单元素写法；
- class的方法名称与函数绑定，这里我们把函数fn绑定到方法名hello上。

通过type()函数创建的类和直接写class是完全一样的，因为Python解释器遇到class定义时，仅仅是扫描一下class定义的语法，然后调用type()函数创建出class。

正常情况下，我们都用class Xxx...来定义类，但是，type()函数也允许我们动态创建出类来，也就是说，动态语言本身支持运行期动态创建类，这和静态语言有非常大的不同，要在静态语言运行期创建类，必须构造源代码字符串再调用编译器，或者借助一些工具生成字节码实现，本质上都是动态编译，会非常复杂。

## metaclass

除了使用type()动态创建类以外，要控制类的创建行为，还可以使用metaclass。

metaclass，直译为元类，简单的解释就是：

当我们定义了类以后，就可以根据这个类创建出实例，所以：先定义类，然后创建实例。

但是如果我们想创建出类呢？那就必须根据metaclass创建出类，所以：先定义metaclass，然后创建类。

连接起来就是：先定义metaclass，就可以创建类，最后创建实例。

所以，metaclass允许你创建类或者修改类。换句话说，你可以把类看成是metaclass创建出来的“实例”。

metaclass是Python面向对象里最难理解，也是最难使用的魔术代码。正常情况下，你不会碰到需要使用metaclass的情况，所以，以下内容看不懂也没关系，因为基本上你不会用到。

我们先看一个简单的例子，这个metaclass可以给我们自定义的MyList增加一个add方法：

定义ListMetaclass，按照默认习惯，metaclass的类名总是以Metaclass结尾，以便清楚地表示这是一个metaclass：

```python
# metaclass是类的模板，所以必须从`type`类型派生：
class ListMetaclass(type):
    def __new__(cls, name, bases, attrs):
        attrs['add'] = lambda self, value: self.append(value)
        return type.__new__(cls, name, bases, attrs)
```

有了ListMetaclass，我们在定义类的时候还要指示使用ListMetaclass来定制类，传入关键字参数metaclass：

```python
class MyList(list, metaclass=ListMetaclass):
    pass
```

当我们传入关键字参数metaclass时，魔术就生效了，它指示Python解释器在创建MyList时，要通过ListMetaclass.__new__()来创建，在此，我们可以修改类的定义，比如，加上新的方法，然后，返回修改后的定义。

__new__()方法接收到的参数依次是：

- 当前准备创建的类的对象；
- 类的名字；
- 类继承的父类集合；
- 类的方法集合。

测试一下MyList是否可以调用add()方法：

```python
>>> L = MyList()
>>> L.add(1)
>> L
[1]
```

而普通的list没有add()方法：

```python
>>> L2 = list()
>>> L2.add(1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'list' object has no attribute 'add'
```

动态修改有什么意义？直接在MyList定义中写上add()方法不是更简单吗？正常情况下，确实应该直接写，通过metaclass修改纯属变态。

但是，总会遇到需要通过metaclass修改类定义的。ORM就是一个典型的例子。

ORM全称“Object Relational Mapping”，即对象-关系映射，就是把关系数据库的一行映射为一个对象，也就是一个类对应一个表，这样，写代码更简单，不用直接操作SQL语句。

要编写一个ORM框架，所有的类都只能动态定义，因为只有使用者才能根据表的结构定义出对应的类来。

让我们来尝试编写一个ORM框架。

编写底层模块的第一步，就是先把调用接口写出来。比如，使用者如果使用这个ORM框架，想定义一个User类来操作对应的数据库表User，我们期待他写出这样的代码：

```python
class User(Model):
    # 定义类的属性到列的映射：
    id = IntegerField('id')
    name = StringField('username')
    email = StringField('email')
    password = StringField('password')

# 创建一个实例：
u = User(id=12345, name='Michael', email='test@orm.org', password='my-pwd')
# 保存到数据库：
u.save()
```

其中，父类Model和属性类型StringField、IntegerField是由ORM框架提供的，剩下的魔术方法比如save()全部由metaclass自动完成。虽然metaclass的编写会比较复杂，但ORM的使用者用起来却异常简单。

现在，我们就按上面的接口来实现该ORM。

首先来定义Field类，它负责保存数据库表的字段名和字段类型：

```python
class Field(object):

    def __init__(self, name, column_type):
        self.name = name
        self.column_type = column_type

    def __str__(self):
        return '<%s:%s>' % (self.__class__.__name__, self.name)
```

在Field的基础上，进一步定义各种类型的Field，比如StringField，IntegerField等等：

```python
class StringField(Field):

    def __init__(self, name):
        super(StringField, self).__init__(name, 'varchar(100)')

class IntegerField(Field):

    def __init__(self, name):
        super(IntegerField, self).__init__(name, 'bigint')
```

下一步，就是编写最复杂的ModelMetaclass了：

```python
class ModelMetaclass(type):

    def __new__(cls, name, bases, attrs):
        if name=='Model':
            return type.__new__(cls, name, bases, attrs)
        print('Found model: %s' % name)
        mappings = dict()
        for k, v in attrs.items():
            if isinstance(v, Field):
                print('Found mapping: %s ==> %s' % (k, v))
                mappings[k] = v
        for k in mappings.keys():
            attrs.pop(k)
        attrs['__mappings__'] = mappings # 保存属性和列的映射关系
        attrs['__table__'] = name # 假设表名和类名一致
        return type.__new__(cls, name, bases, attrs)
```

以及基类Model：

```python
class Model(dict, metaclass=ModelMetaclass):

    def __init__(self, **kw):
        super(Model, self).__init__(**kw)

    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttributeError(r"'Model' object has no attribute '%s'" % key)

    def __setattr__(self, key, value):
        self[key] = value

    def save(self):
        fields = []
        params = []
        args = []
        for k, v in self.__mappings__.items():
            fields.append(v.name)
            params.append('?')
            args.append(getattr(self, k, None))
        sql = 'insert into %s (%s) values (%s)' % (self.__table__, ','.join(fields), ','.join(params))
        print('SQL: %s' % sql)
        print('ARGS: %s' % str(args))
```

当用户定义一个class User(Model)时，Python解释器首先在当前类User的定义中查找metaclass，如果没有找到，就继续在父类Model中查找metaclass，找到了，就使用Model中定义的metaclass的ModelMetaclass来创建User类，也就是说，metaclass可以隐式地继承到子类，但子类自己却感觉不到。

在ModelMetaclass中，一共做了几件事情：

排除掉对Model类的修改；

在当前类（比如User）中查找定义的类的所有属性，如果找到一个Field属性，就把它保存到一个__mappings__的dict中，同时从类属性中删除该Field属性，否则，容易造成运行时错误（实例的属性会遮盖类的同名属性）；

把表名保存到__table__中，这里简化为表名默认为类名。

在Model类中，就可以定义各种操作数据库的方法，比如save()，delete()，find()，update等等。

我们实现了save()方法，把一个实例保存到数据库中。因为有表名，属性到字段的映射和属性值的集合，就可以构造出INSERT语句。

编写代码试试：

```python
u = User(id=12345, name='Michael', email='test@orm.org', password='my-pwd')
u.save()
```

输出如下：

```python
Found model: User
Found mapping: email ==> <StringField:email>
Found mapping: password ==> <StringField:password>
Found mapping: id ==> <IntegerField:uid>
Found mapping: name ==> <StringField:username>
SQL: insert into User (password,email,username,id) values (?,?,?,?)
ARGS: ['my-pwd', 'test@orm.org', 'Michael', 12345]
```

可以看到，save()方法已经打印出了可执行的SQL语句，以及参数列表，只需要真正连接到数据库，执行该SQL语句，就可以完成真正的功能。

不到100行代码，我们就通过metaclass实现了一个精简的ORM框架，是不是非常简单？

# 异常处理

Python有两种错误很容易辨认：语法错误和异常。

## 语法错误
Python 的语法错误或者称之为解析错，是初学者经常碰到的，如下实例

```python
>>> while True print('Hello world')
  File "<stdin>", line 1, in ?
    while True print('Hello world')
                   ^
SyntaxError: invalid syntax
```

这个例子中，函数 `print()` 被检查到有错误，是它前面缺少了一个冒号（:）。

语法分析器指出了出错的一行，并且在最先找到的错误的位置标记了一个小小的箭头。

## 异常

即便Python程序的语法是正确的，在运行它的时候，也有可能发生错误。运行期检测到的错误被称为异常。

大多数的异常都不会被程序处理，都以错误信息的形式展现在这里:

```python
>>> 10 * (1/0)
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ZeroDivisionError: division by zero
>>> 4 + spam*3
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'spam' is not defined
>>> '2' + 2
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: Can't convert 'int' object to str implicitly
```

异常以不同的类型出现，这些类型都作为信息的一部分打印出来: 例子中的类型有 `ZeroDivisionError`，`NameError` 和 `TypeError`。

错误信息的前面部分显示了异常发生的上下文，并以调用栈的形式显示具体信息。

## 异常处理
以下例子中，让用户输入一个合法的整数，但是允许用户中断这个程序（使用 Control-C 或者操作系统提供的方法）。用户中断的信息会引发一个 `KeyboardInterrupt` 异常。

```python
>>> while True:
        try:
            x = int(input("Please enter a number: "))
            break
        except ValueError:
            print("Oops!  That was no valid number.  Try again   ")
```

try语句按照如下方式工作；

- 首先，执行try子句（在关键字try和关键字except之间的语句）
- 如果没有异常发生，忽略except子句，try子句执行后结束。
- 如果在执行try子句的过程中发生了异常，那么try子句余下的部分将被忽略。如果异常的类型和 except 之后的名称相符，那么对应的except子句将被执行。最后执行 try 语句之后的代码。
- 如果一个异常没有与任何的except匹配，那么这个异常将会传递给上层的try中。
- 一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

处理程序将只针对对应的try子句中的异常进行处理，而不是其他的 try 的处理程序中的异常。

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

try except 语句还有一个可选的else子句，如果使用这个子句，那么必须放在所有的except子句之后。这个子句将在try子句没有发生任何异常的时候执行。例如:

```python
for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except IOError:
        print('cannot open', arg)
    else:
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

使用 else 子句比把所有的语句都放在 try 子句里面要好，这样可以避免一些意想不到的、而except又没有捕获的异常。

异常处理并不仅仅处理那些直接发生在try子句中的异常，而且还能处理子句中调用的函数（甚至间接调用的函数）里抛出的异常。例如:

```python
>>> def this_fails():
        x = 1/0
   
>>> try:
        this_fails()
    except ZeroDivisionError as err:
        print('Handling run-time error:', err)
   
Handling run-time error: int division or modulo by zero
```

## 抛出异常

Python 使用 raise 语句抛出一个指定的异常。例如:

```python
>>> raise NameError('HiThere')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: HiThere
```

raise 唯一的一个参数指定了要被抛出的异常。它必须是一个异常的实例或者是异常的类（也就是 Exception 的子类）。

如果你只想知道这是否抛出了一个异常，并不想去处理它，那么一个简单的 raise 语句就可以再次把它抛出。

```python
>>> try:
        raise NameError('HiThere')
    except NameError:
        print('An exception flew by!')
        raise
   
An exception flew by!
Traceback (most recent call last):
  File "<stdin>", line 2, in ?
NameError: HiThere
```

## 用户自定义异常

你可以通过创建一个新的异常类来拥有自己的异常。异常类继承自 Exception 类，可以直接继承，或者间接继承，例如:

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

在这个例子中，类 Exception 默认的 __init__() 被覆盖。

当创建一个模块有可能抛出多种不同的异常时，一种通常的做法是为这个包建立一个基础异常类，然后基于这个基础类为不同的错误情况创建不同的子类:

```python
class Error(Exception):
    """Base class for exceptions in this module."""
    pass
 
class InputError(Error):
    """Exception raised for errors in the input.
 
    Attributes:
        expression -- input expression in which the error occurred
        message -- explanation of the error
    """
 
    def __init__(self, expression, message):
        self.expression = expression
        self.message = message
 
class TransitionError(Error):
    """Raised when an operation attempts a state transition that's not
    allowed.
 
    Attributes:
        previous -- state at beginning of transition
        next -- attempted new state
        message -- explanation of why the specific transition is not allowed
    """
 
    def __init__(self, previous, next, message):
        self.previous = previous
        self.next = next
        self.message = message
```

大多数的异常的名字都以"Error"结尾，就跟标准的异常命名一样。

## 定义清理行为

try 语句还有另外一个可选的子句，它定义了无论在任何情况下都会执行的清理行为。 例如:

```python
>>> try:
...     raise KeyboardInterrupt
... finally:
...     print('Goodbye, world!')
... 
Goodbye, world!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
KeyboardInterrupt
```

以上例子不管 try 子句里面有没有发生异常，finally 子句都会执行。

如果一个异常在 try 子句里（或者在 except 和 else 子句里）被抛出，而又没有任何的 except 把它截住，那么这个异常会在 finally 子句执行后再次被抛出。

下面是一个更加复杂的例子（在同一个 try 语句里包含 except 和 finally 子句）:

```python
>>> def divide(x, y):
        try:
            result = x / y
        except ZeroDivisionError:
            print("division by zero!")
        else:
            print("result is", result)
        finally:
            print("executing finally clause")
   
>>> divide(2, 1)
result is 2.0
executing finally clause
>>> divide(2, 0)
division by zero!
executing finally clause
>>> divide("2", "1")
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```

## 预定义的清理行为

一些对象定义了标准的清理行为，无论系统是否成功的使用了它，一旦不需要它了，那么这个标准的清理行为就会执行。

这面这个例子展示了尝试打开一个文件，然后把内容打印到屏幕上:

```python
for line in open("myfile.txt"):
    print(line, end="")
```

以上这段代码的问题是，当执行完毕后，文件会保持打开状态，并没有被关闭。

关键词 with 语句就可以保证诸如文件之类的对象在使用完之后一定会正确的执行他的清理方法:

```python
with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
```

以上这段代码执行完毕后，就算在处理过程中出问题了，文件 f 总是会关闭。

# 拷贝

Assignment statements in Python do not copy objects, they create bindings between a target and an object. For collections that are mutable or contain mutable items, a copy is sometimes needed so one can change one copy without changing the other. This module provides generic shallow and deep copy operations (explained below).

Interface summary:

```python
copy.copy(x)
```

Return a shallow copy of `x`.

```python
copy.deepcopy(x[, memo])
```

Return a deep copy of `x`.

```python
exception copy.error
```

Raised for module specific errors.

The difference between shallow and deep copying is only relevant for compound objects (objects that contain other objects, like lists or class instances):

- A shallow copy constructs a new compound object and then (to the extent possible) inserts references into it to the objects found in the original.
- A deep copy constructs a new compound object and then, recursively, inserts copies into it of the objects found in the original.

Two problems often exist with deep copy operations that don’t exist with shallow copy operations:

- Recursive objects (compound objects that, directly or indirectly, contain a reference to themselves) may cause a recursive loop.
- Because deep copy copies everything it may copy too much, such as data which is intended to be shared between copies.

The `deepcopy()` function avoids these problems by:

- keeping a memo dictionary of objects already copied during the current copying pass; and
- letting user-defined classes override the copying operation or the set of components copied.

This module does not copy types like module, method, stack trace, stack frame, file, socket, window, array, or any similar types. It does “copy” functions and classes (shallow and deeply), by returning the original object unchanged; this is compatible with the way these are treated by the pickle module.

Shallow copies of dictionaries can be made using dict.copy(), and of lists by assigning a slice of the entire list, for example, copied_list = original_list[:].

In order for a class to define its own copy implementation, it can define special methods `__copy__()` and `__deepcopy__()`. The former is called to implement the shallow copy operation; no additional arguments are passed. The latter is called to implement the deep copy operation; it is passed one argument, the memo dictionary. If the `__deepcopy__()` implementation needs to make a deep copy of a component, it should call the `deepcopy()` function with the component as first argument and the memo dictionary as second argument.

# 循环技巧

When looping through dictionaries, the key and corresponding value can be retrieved at the same time using the items() method.

```python
>>>
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

When looping through a sequence, the position index and corresponding value can be retrieved at the same time using the enumerate() function.

```python
>>>
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```

To loop over two or more sequences at the same time, the entries can be paired with the zip() function.

```python
>>>
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```

To loop over a sequence in reverse, first specify the sequence in a forward direction and then call the reversed() function.

```python
>>>
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```

To loop over a sequence in sorted order, use the sorted() function which returns a new sorted list while leaving the source unaltered.

```python
>>>
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```

It is sometimes tempting to change a list while you are looping over it; however, it is often simpler and safer to create a new list instead.

```python
>>>
>>> import math
>>> raw_data = [56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]
>>> filtered_data = []
>>> for value in raw_data:
...     if not math.isnan(value):
...         filtered_data.append(value)
...
>>> filtered_data
[56.2, 51.7, 55.3, 52.5, 47.8]
```


# 正则表达式

见[菜鸟教程-正则表达式](http://www.runoob.com/python3/python3-reg-expressions.html)

# OS 模块

见[菜鸟教程-OS](http://www.runoob.com/python3/python3-os-file-methods.html)

# 内建函数

## 所有内建函数

<table>
<colgroup><col width="21%"><col width="18%"><col width="20%"><col width="20%"><col width="22%"></colgroup>
<thead valign="bottom"><tr><th colspan="5">Built-in Functions (链接为官方文档)</th></tr></thead>
<tbody valign="top">
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#abs"><code>abs()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#delattr"><code>delattr()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#hash"><code>hash()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-memoryview"><code>memoryview()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-set"><code>set()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#all"><code>all()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-dict"><code>dict()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#help"><code>help()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#min"><code>min()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#setattr"><code>setattr()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#any"><code>any()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#dir"><code>dir()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#hex"><code>hex()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#next"><code>next()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#slice"><code>slice()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#ascii"><code>ascii()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#divmod"><code>divmod()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#id"><code>id()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#object"><code>object()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#sorted"><code>sorted()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#bin"><code>bin()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#enumerate"><code>enumerate()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#input"><code>input()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#oct"><code>oct()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#staticmethod"><code>staticmethod()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#bool"><code>bool()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#eval"><code>eval()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#int"><code>int()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#open"><code>open()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-str"><code>str()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#breakpoint"><code>breakpoint()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#exec"><code>exec()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#isinstance"><code>isinstance()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#ord"><code>ord()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#sum"><code>sum()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#func-bytearray"><code>bytearray()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#filter"><code>filter()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#issubclass"><code>issubclass()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#pow"><code>pow()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#super"><code>super()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#func-bytes"><code>bytes()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#float"><code>float()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#iter"><code>iter()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#print"><code>print()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-tuple"><code>tuple()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#callable"><code>callable()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#format"><code>format()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#len"><code>len()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#property"><code>property()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#type"><code>type()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#chr"><code>chr()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-frozenset"><code>frozenset()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-list"><code>list()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#func-range"><code>range()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#vars"><code>vars()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#classmethod"><code>classmethod()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#getattr"><code>getattr()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#locals"><code>locals()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#repr"><code>repr()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#zip"><code>zip()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#compile"><code>compile()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#globals"><code>globals()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#map"><code>map()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#reversed"><code>reversed()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#__import__"><code>__import__()</code></a></td></tr>
<tr><td><a href="https://docs.python.org/3.7/library/functions.html#complex"><code>complex()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#hasattr"><code>hasattr()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#max"><code>max()</code></a></td>
<td><a href="https://docs.python.org/3.7/library/functions.html#round"><code>round()</code></a></td><td>&nbsp;</td></tr>
</tbody></table>

## 属性相关

### `getattr(object, name[, default])`
Return the value of the named attribute of `object`. `name` must be a string. If the string is the name of one of the object’s attributes, the result is the value of that attribute. For example, `getattr(x, 'foobar')` is equivalent to `x.foobar`. If the named attribute does not exist, default is returned if provided, otherwise `AttributeError` is raised.

### `setattr(object, name, value)`
This is the counterpart of `getattr()`. The arguments are an object, a string and an arbitrary value. The string may name an existing attribute or a new attribute. The function assigns the value to the attribute, provided the object allows it. For example, `setattr(x, 'foobar', 123)` is equivalent to `x.foobar = 123`.

### `delattr(object, name)`
This is a relative of `setattr()`. The arguments are an object and a string. The string must be the name of one of the object’s attributes. The function deletes the named attribute, provided the object allows it. For example, `delattr(x, 'foobar')` is equivalent to del `x.foobar`.

### `hasattr(object, name)`
The arguments are an object and a string. The result is `True` if the string is the name of one of the object’s attributes, `False` if not. (This is implemented by calling `getattr(object, name)` and seeing whether it raises an AttributeError or not.)

### `dir([object])`
Without arguments, return the list of names in the current local scope. With an argument, attempt to return a list of valid attributes for that object.

If the object has a method named `__dir__()`, this method will be called and must return the list of attributes. This allows objects that implement a custom `__getattr__()` or `__getattribute__()` function to customize the way `dir()` reports their attributes.

If the object does not provide `__dir__()`, the function tries its best to gather information from the object’s `__dict__` attribute, if defined, and from its type object. The resulting list is not necessarily complete, and may be inaccurate when the object has a custom `__getattr__()`.

The default `dir()` mechanism behaves differently with different types of objects, as it attempts to produce the most relevant, rather than complete, information:

- If the object is a module object, the list contains the names of the module’s attributes.
- If the object is a type or class object, the list contains the names of its attributes, and recursively of the attributes of its bases.
- Otherwise, the list contains the object’s attributes’ names, the names of its class’s attributes, and recursively of the attributes of its class’s base classes.

The resulting list is sorted alphabetically. For example:

```python
>>> import struct
>>> dir()   # show the names in the module namespace  # doctest: +SKIP
['__builtins__', '__name__', 'struct']
>>> dir(struct)   # show the names in the struct module # doctest: +SKIP
['Struct', '__all__', '__builtins__', '__cached__', '__doc__', '__file__',
 '__initializing__', '__loader__', '__name__', '__package__',
 '_clearcache', 'calcsize', 'error', 'pack', 'pack_into',
 'unpack', 'unpack_from']
>>> class Shape:
...     def __dir__(self):
...         return ['area', 'perimeter', 'location']
>>> s = Shape()
>>> dir(s)
['area', 'location', 'perimeter']
```

### `globals()`
Return a dictionary representing the current global symbol table. This is always the dictionary of the current module (inside a function or method, this is the module where it is defined, not the module from which it is called).

### `locals()`
Update and return a dictionary representing the current local symbol table. Free variables are returned by `locals()` when it is called in function blocks, but not in class blocks.

### `vars([object])`
Return the `__dict__` attribute for a module, class, instance, or any other object with a `__dict__` attribute.

Without an argument, `vars()` acts like `locals()`. Note, the locals dictionary is only useful for reads since updates to the locals dictionary are ignored.

## 迭代相关

### `sum(iterable[, start])`
Sums start and the items of an iterable from left to right and returns the total. start defaults to 0. The iterable’s items are normally numbers, and the start value is not allowed to be a string.The preferred, fast way to concatenate a sequence of strings is by calling `''.join(sequence)`.

### `sorted(iterable, *, key=None, reverse=False)`
Return a new sorted list from the items in iterable.

Has two optional arguments which must be specified as keyword arguments.

key specifies a function of one argument that is used to extract a comparison key from each element in iterable (for example, `key=str.lower`). The default value is `None` (compare the elements directly).

对于dict使用sorted：
```python
>>> d = {'data1':3, 'data2':1, 'data3':2, 'data4':4}  
>>> sorted(d.items())
[('data1', 3), ('data2', 1), ('data3', 2), ('data4', 4)]
>>> sorted(d.items(), key=lambda x: x[1])
[('data2', 1), ('data3', 2), ('data1', 3), ('data4', 4)]
```

reverse is a boolean value. If set to `True`, then the list elements are sorted as if each comparison were reversed.

The built-in `sorted()` function is guaranteed to be stable. A sort is stable if it guarantees not to change the relative order of elements that compare equal — this is helpful for sorting in multiple passes (for example, sort by department, then by salary grade).

### `reversed(seq)`
Return a reverse iterator. seq must be an object which has a `__reversed__()` method or supports the sequence protocol (the `__len__()` method and the `__getitem__()` method with integer arguments starting at 0).

### `enumerate(iterable, start=0)`
Return an enumerate object. iterable must be a sequence, an iterator, or some other object which supports iteration. The `__next__()` method of the iterator returned by enumerate() returns a tuple containing a count (from start which defaults to 0) and the values obtained from iterating over iterable.

```python
>>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

Equivalent to:

```python
def enumerate(sequence, start=0):
    n = start
    for elem in sequence:
        yield n, elem
        n += 1
```

### `zip(*iterables)`
Make an iterator that aggregates elements from each of the iterables.

Returns an iterator of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables. The iterator stops when the shortest input iterable is exhausted. With a single iterable argument, it returns an iterator of 1-tuples. With no arguments, it returns an empty iterator. Equivalent to:

```python
def zip(*iterables):
    # zip('ABCD', 'xy') --> Ax By
    sentinel = object()
    iterators = [iter(it) for it in iterables]
    while iterators:
        result = []
        for it in iterators:
            elem = next(it, sentinel)
            if elem is sentinel:
                return
            result.append(elem)
        yield tuple(result)
```

The left-to-right evaluation order of the iterables is guaranteed. This makes possible an idiom for clustering a data series into n-length groups using `zip(*[iter(s)]*n)`. This repeats the same iterator n times so that each output tuple has the result of n calls to the iterator. This has the effect of dividing the input into n-length chunks.

`zip()` should only be used with unequal length inputs when you don’t care about trailing, unmatched values from the longer iterables.

`zip()` in conjunction with the `*` operator can be used to unzip a list:

```python
>>>
>>> x = [1, 2, 3]
>>> y = [4, 5, 6]
>>> zipped = zip(x, y)
>>> list(zipped)
[(1, 4), (2, 5), (3, 6)]
>>> x2, y2 = zip(*zip(x, y))
>>> x == list(x2) and y == list(y2)
True
```

### `map(function, iterable, ...)`
Return an iterator that applies function to every item of iterable, yielding the results. If additional iterable arguments are passed, function must take that many arguments and is applied to the items from all iterables in parallel. With multiple iterables, the iterator stops when the shortest iterable is exhausted. 

### `filter(function, iterable)`
Construct an iterator from those elements of iterable for which function returns true. iterable may be either a sequence, a container which supports iteration, or an iterator. If function is None, the identity function is assumed, that is, all elements of iterable that are false are removed.

Note that `filter(function, iterable)` is equivalent to the generator expression (`item for item in iterable if function(item)`) if function is not None and (`item for item in iterable if item`) if function is None.

## 其他

### `all(iterable)`
Return `True` if all elements of the iterable are true (or if the iterable is empty). Equivalent to:

```python
def all(iterable):
    for element in iterable:
        if not element:
            return False
    return True
```

### `any(iterable)`
Return `True` if any element of the iterable is true. If the iterable is empty, return `False`. Equivalent to:

```python
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```

### `callable(object)`
Return `True` if the object argument appears callable, `False` if not. If this returns true, it is still possible that a call fails, but if it is false, calling object will never succeed. Note that classes are callable (calling a class returns a new instance); instances are callable if their class has a `__call__()` method.

### `divmod(a, b)`

```
Take two (non complex) numbers as arguments and return a pair of numbers consisting of their quotient and remainder when using integer division. With mixed operand types, the rules for binary arithmetic operators apply. For integers, the result is the same as (a // b, a % b). For floating point numbers the result is (q, a % b), where q is usually math.floor(a / b) but may be 1 less than that. In any case q * b + a % b is very close to a, if a % b is non-zero it has the same sign as b, and 0 <= abs(a % b) < abs(b).
```

### `hash(object)`
Return the hash value of the object (if it has one). Hash values are integers. They are used to quickly compare dictionary keys during a dictionary lookup. Numeric values that compare equal have the same hash value (even if they are of different types, as is the case for 1 and 1.0).

Note For objects with custom `__hash__()` methods, note that `hash()` truncates the return value based on the bit width of the host machine.


### `class slice(stop)`
### `class slice(start, stop[, step])`
Return a slice object representing the set of indices specified by `range(start, stop, step)`. The `start` and `step` arguments default to `None`. Slice objects have read-only data attributes start, stop and step which merely return the argument values (or their default). Slice objects are also generated when extended indexing syntax is used. For example: `a[start:stop:step]`.

# IO

[官方文档 - 格式化输出 & 文件IO](https://docs.python.org/3/tutorial/inputoutput.html)

[官方文档 - 格式化输出用法](https://docs.python.org/3/library/string.html#formatspec)

# map reduce filter 讲解

[廖雪峰 - map & reduce](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317852443934a86aa5bb5ea47fbbd5f35282b331335000)

[廖雪峰 - filter](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431821084171d2e0f22e7cc24305ae03aa0214d0ef29000)

# 日期和时间

[菜鸟教程 - 日期和时间](http://www.runoob.com/python3/python3-date-time.html)
