title: Python 类型判断
date: 2016-03-24 08:08:45
tags:
- Python
- 类型判断
---

## type
  type 只是判断这个类型。
  ``` Python
  >>>lst = [1, 2, 3]
  >>>type(lst)
  <type 'list'>
  ```

## ininstance
  isinstance 可以判断是不是已知的类型，

  ``` bash
   isinstance(object, class-or-type-or-tuple) -> bool  
   /* Return whether an object is an instance of a class or of a subclass thereof. */
  ```
  参数二为一个元组，则若对象类型与元组中类型名之一相同即返回True.
  ``` Python
  >>>isinstance(lst, list)
  True
  >>>isinstance(lst, (int, str, list))
  True
  >>>isinstance(lst, (int, str, list))
  True
  ```
