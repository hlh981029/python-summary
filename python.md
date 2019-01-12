# 没查的
在咱们的考试里面 一律以python3为标准

- [ ] 方法 函数
- [ ] python 只读 两种方法
- [ ] 属性 @propery @a.setter a = property()
- [ ] 描述器
- [ ] zip()
- [ ] 切片
- [ ] 实例属性 类属性
- [ ] 元类
- [ ] sort reverse
- [ ] reduce filter python 2 & 3
- [ ] yield from
- [ ] 装饰器
- [ ] copy deepcopy
- [ ] 元组可以省略括号
- [ ] 类装饰器 __call\_\_
- [ ] 闭包是个什么概念 拆包打包
- [ ] 迭代器
- [ ] 异常处理
- [ ] os模块
- [ ] map reduce filter lambda

# 基本数据类型

## 标准数据类型

Python3 中有六个标准的数据类型：
- Number（数字）
    - int、float、bool、complex（复数）
- String（字符串）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

Python3 的六个标准数据类型中：
- **不可变数据（3 个）**：Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）**：List（列表）、Dictionary（字典）、Set（集合）。

## 查询变量类型

内置的 `type()` 函数可以用来查询变量所指的对象类型。

```python
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

此外还可以用 `isinstance()` 来判断：

```python
>>>a = 111
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

## Python数据类型转换

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
<table>
<tbody>
<tr><th>运算符</th><th>描述</th><th>实例</th></tr>
<tr><td>**</td><td>幂 - 返回x的y次幂</td><td> a**b 为10的21次方</td></tr>
<tr><td>//</td><td>取整除 - 向下取接近除数的整数</td><td>

```python
>>> 9//2
4
>>> -9//2
-5
```

</td></tr>
</tbody></table>

## 比较运算符

- `==`
- `!=`
- `>`
- `<`
- `>=`
- `<=`

## 赋值运算符

### 元组与列表

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

### 列表的`append()`与`extend()`

```python
>>> a = (1, 2, 3)
>>> b = [1, 2, 3]
>>>
>>> b.append(a)
>>> b
[1, 2, 3, (1, 2, 3)]
>>> b.extend(a)
>>> b
[1, 2, 3, (1, 2, 3), 1, 2, 3]
```
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

```python
>>> a is b
True
>>> a is not b
False
>>> a not is b
  File "<stdin>", line 1
    a not is b
           ^
SyntaxError: invalid syntax
>>>
```

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

# 列表

Python包含以下函数:

<table class="reference">
<tbody><tr>
<th style="width:5%">序号</th><th style="width:95%">函数</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-list-len.html">len(list)</a><br>列表元素个数</td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-list-max.html">max(list)</a><br>返回列表元素最大值</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-list-min.html">min(list)</a><br>返回列表元素最小值</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-list-list.html">list(seq)</a><br>将元组转换为列表</td></tr>
</tbody></table>

Python包含以下方法:

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

# 字典

Python字典包含了以下内置函数：

<table>
<tbody><tr>
<th width="5%">序号</th><th width="25%">函数及描述</th><th>实例</th></tr>
<tr><td>1</td><td>len(dict)<br>计算字典元素个数，即键的总数。</td><td>

```python
>>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
>>> len(dict)
3
```

</td></tr>
<tr><td>2</td><td>str(dict)<br>输出字典，以可打印的字符串表示。</td><td>

```python
>>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
>>> str(dict)
"{'Name': 'Runoob', 'Class': 'First', 'Age': 7}"
```

</td></tr>
<tr><td>3</td><td>type(variable)<br>返回输入的变量类型，如果变量是字典就返回字典类型。</td><td>

```python
>>> dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
>>> type(dict)
<class 'dict'>;
```

</td></tr>
</tbody></table>

Python字典包含了以下内置方法：

<table>
<tbody>
<tr><th style="width:5%">序号</th><th style="width:95%">函数及描述</th></tr>
<tr><td>1</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-clear.html">radiansdict.clear()</a><br>删除字典内所有元素 </td></tr>
<tr><td>2</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-copy.html">radiansdict.copy()</a><br>返回一个字典的浅复制</td></tr>
<tr><td>3</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-fromkeys.html">radiansdict.fromkeys()</a><br> 创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值</td></tr>
<tr><td>4</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-get.html">radiansdict.get(key, default=None)</a><br>返回指定键的值，如果值不在字典中返回default值</td></tr>
<tr><td>5</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-in.html">key in dict</a><br>如果键在字典dict里返回true，否则返回false</td></tr>
<tr><td>6</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-items.html">radiansdict.items()</a><br>以列表返回可遍历的(键, 值) 元组数组</td></tr>
<tr><td>7</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-keys.html">radiansdict.keys()</a><br>返回一个迭代器，可以使用 list() 来转换为列表</td></tr>
<tr><td>8</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-setdefault.html">radiansdict.setdefault(key, default=None)</a><br>和get()类似, 但如果键不存在于字典中，将会添加键并将值设为default</td></tr>
<tr><td>9</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-update.html">radiansdict.update(dict2)</a><br>把字典dict2的键/值对更新到dict里</td></tr>
<tr><td>10</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-values.html">radiansdict.values()</a><br>返回一个迭代器，可以使用 list() 来转换为列表</td></tr>
<tr><td>11</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-pop.html">pop(key[,default])</a><br>删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。否则，返回default值。</td></tr>
<tr><td>12</td><td><a href="http://www.runoob.com/python3/python3-att-dictionary-popitem.html"> popitem()</a><br>随机返回并删除字典中的一对键和值(一般删除末尾对)。</td></tr>
</tbody></table>			
