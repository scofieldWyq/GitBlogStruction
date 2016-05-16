title: Python 字符串转换成字典
date: 2016-03-24 08:12:20
tags:
- Python
- string
- dict
- dictionary
- str

---
## 如何将一个字符串(string)转为字典(dict)呢?
  > 只要用 eval()或exec() 函数就可以实现了

  ``` Python
    >>> a = "{'a': 'hi', 'b': 'there'}"
    >>> b = eval(a)
    >>> b
    {'a': 'hi', 'b': 'there'}
    >>> exec ("c=" + a)
    >>> c
    {'a': 'hi', 'b': 'there'}
    >>>
  ```

## 参考链接

- [Python中将字符串类型转为字典类型（string to dict）](http://www.pythonclub.org/python-hacks/string2dict)
