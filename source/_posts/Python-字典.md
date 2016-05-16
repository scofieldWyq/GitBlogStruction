title: Python 字典
date: 2016-03-23 22:14:19
tags:
- Python
- dict
- dictionary

---
## 过程

   在字典中，先根据需求来获得字典，然后就是先使用它增删查改，然后就是一些主意的事项了。
   [创建字典](#create)
   [查询字典内容](#search)
   [更改字典的值](#change)
   [删除字典的值](#delete)
   [字典内置的函数&方法](#method)

## 简单介绍字典的用途

   在数据中，具有键-值（key-value）存储，具有极快的查找速度。使用字典，我们就可以通过字符串来获取到我们想要的信息。


---

## <span id="create">创建字典</span>

   字典是有键值对组成的一种容器。那如何创建它呢？
   ``` Python
   >>> dict = {'d1':'dict1', 'd2':'dict2', 'd3':'dict3', 'd4':'dict4'}
   >>> print dict
   ```

   结果如下
   ``` bash
   {'d4': 'dict4', 'd2': 'dict2', 'd3': 'dict3', 'd1': 'dict1'}
   ```

   这样，我们的字典创建就可以了，以key-value 的形式作为元素哦。

## 关于字典的键(key)   
   value 可以没有限制地取任何python对象，但是 key 就需要记住两个：

   1. 不允许同一个键出现`两次`。创建时如果同一个键被赋值两次，`后一个值会被记住`。
   ``` python
    >>> dict = {'name':'hello', 'name':'oh'}
    >>> print dict
    {'name': 'oh'}
    # 只有一个值，那就是最后同名的那个值
   ```  

   2. `键`必须不可变，所以可以用`数`，`字符串`或`元组`充当。
   ``` python
   >>> dict = {8:'bye', 'you':'coder'} # 包括了 数 '8'， 字符串 'you'
   >>> print dict
   {8: 'bye', 'you': 'coder'}
   >>> print 'dict[8]' + dict[8] + ', dict[\'you\']' + dict['you']
   dict[8]bye, dict['you']coder
   ```

---

## <span id="search">查询字典的值</span>

  **字典的查询就不难了，依照上面的字典。试一试**
    ``` Python
    >>> dict = {8:'bye', 'you':'coder'} # 包括了 数 '8'， 字符串 'you'
    >>> dict[8]
    'bye'
    >>> dict['you']
    'coder'
    ```

  通过键我们就可以访问到字典对应的值了，不会像数组那样从 `index 0` 开始了。

  **但是如果我们查询的键没有呢？就会出错。**
    ``` python
    >>> dict[9]
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    KeyError: 9
    ```


  那么怎么样才知道它有没有这个`键(key)`呢? 使用方法 `has_key([key])`
    ``` python
    >>> dict.has_key(9)
    False
    >>> dict.has_key(8)
    True
    # 这样我们就可以在脚本中去判断键的存在咯。
    ```
  **那如果出现Python Error:TypeError: string indices must be integers, not str呢**
    请参照[Python Error:TypeError: string indices must be integers, not str](http://scofieldwyq.github.io/2016/03/23/Python-Error-TypeError-string-indices-must-be-integers-not-str/)

---

## <span id="change">更改字典的值</span>
  **修改字典的值，就很容易了。获取到对应键的值，再赋值就好了。**
    ``` Python
    >>> print dict[8]
    bye
    >>> dict[8]=80
    >>> print dict[8]
    80
    ```

  结果就是这样简单啦。

---

## <span id="delete">删除字典的值</span>
  删除字典有两种
  1. 删除单一元素 `del`
    ``` python
    >>> dict = {8:'bye', 'you':'coder'}
    >>> print dict
    {8: 'bye', 'you': 'coder'}
    >>> del dict[8] # 删除元素
    >>> print dict
    {'you': 'coder'}
    ```
  2. 清空字典 `dict-instance.clear()`
    ``` Python
    >>> dict = {8:'bye', 'you':'coder'}
    >>> dict.clear() # 清空字典元素啦。。。。
    >>> print dict
    {}
    ```

---

## <span id="method">字典内置的函数&方法</span>
  **内置函数**
    ``` python
      cmp(dict1, dict2)：  比较两个字典元素。

      len(dict)：          计算字典元素个数，即键的总数。

      str(dict)：          输出字典可打印的字符串表示。

      type(variable)：     返回输入的变量类型，如果变量是字典就返回字典类型。
    ```


  **Python字典包含了以下内置方法：**
    ```python
      radiansdict.clear()：                      删除字典内所有元素

      radiansdict.copy()：                       返回一个字典的浅复制

      radiansdict.fromkeys()：                   创建一个新字典，以序列seq中元素做字典的键，val为字典所有键对应的初始值

      radiansdict.get(key, default=None)：       返回指定键的值，如果值不在字典中返回default值

      radiansdict.has_key(key)：                 如果键在字典dict里返回true，否则返回false

      radiansdict.items()：                      以列表返回可遍历的(键, 值) 元组数组

      radiansdict.keys()：                       以列表返回一个字典所有的键

      radiansdict.setdefault(key, default=None)：和get()类似, 但如果键不已经存在于字典中，将会添加键并将值设为default

      radiansdict.update(dict2)：                把字典dict2的键/值对更新到dict里

      radiansdict.values()：                     以列表返回字典中的所有值
    ```
## 参考链接
- [Python 字典(Dictionary)操作详解](http://www.jb51.net/article/47990.htm)
- [使用dict和set](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/0013868193482529754158abf734c00bba97c87f89a263b000)
- [python通过字典dict判断指定键值是否存在的方法](http://www.jb51.net/article/62610.htm)
