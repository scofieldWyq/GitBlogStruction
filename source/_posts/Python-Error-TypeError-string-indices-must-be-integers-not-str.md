title: 'Python Error:TypeError: string indices must be integers, not str'
date: 2016-03-23 22:17:20
tags:
- Python
- dict
- dictionary
- Error

---

## 这个情况出现的原因

   由于当前的'字典'并不是字典，而是字符串。导致了拿字典的访问方法去访问字符串就会出现访问字典的
  下标，字典的下标是数字而不是字符串。所以出错了。

---

## 解决问题

   再次确认一下你的字典是否是真的字典，还是一个字符串。最好 `debug` 一下

---

## 实践例子
  这是一个长得跟字典很像的家伙
  ``` Python
  >>> dict = "{8:'bye', 'you':'coder'}" #假字典 fake
  >>> dict_real = {8:'bye', 'you':'coder'} # 真字典 real
  >>> print dict
  {8:'bye', 'you':'coder'} # 哟呵，输出
  >>> print dict_real
  {8: 'bye', 'you': 'coder'} # 这是真字典的输出。
  # 然后我们来获取键 'you'的值
  # 真字典情况
  >>> print dict_real['you']
  coder # 没有问题哦，
  # 看看假字典的真面目啦。。。。。。
  >>> print dict['you']
  Traceback (most recent call last): # 错误咯，这就是原因啦。
    File "<stdin>", line 1, in <module>
  TypeError: string indices must be integers, not str
  ```

##参考链接
- [TypeError: string indices must be integers, not str // working with dict](http://stackoverflow.com/questions/18931315/typeerror-string-indices-must-be-integers-not-str-working-with-dict)
