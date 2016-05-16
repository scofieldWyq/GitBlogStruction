title: Python setattr 使用和分析
date: 2016-03-22 10:13:33
tags:
- Python
- setattr

---

## setattr 讲解
``` Python
 setattr(	object, name, value)

 # 参数就是一个对象，name是可能是现有的属性或者是一个可以新建的属性，value为该属性的值。
 #
 # 这样，我们可以动态的生成属性
 # 记住，name 和 value 都是字符串值哦。

```

## setattr 实践

  [代码来源](https://raw.githubusercontent.com/scofieldWyq/wyqBlog/master/code/py_setattr.py)
  首先，去掉 第15行的注释运行,结果显示如下
  ``` bash
  $ python py_setattr.py
  attr4 exists?
  Traceback (most recent call last):
    File "py_setattr.py", line 15, in <module>
      print T.attr4
  AttributeError: 'test' object has no attribute 'attr4'
  ```

  再加上注释，运行
  ``` bash
  $ python py_setattr.py                        
  attr4 exists?
  create new attribute <attr4> test4
  attribute <attr3>:test3
  changed attribute <attr3> :test3_changed
  ```
## 参考链接
- [Python的getattr(),setattr(),delattr(),hasattr()](http://www.cnblogs.com/zhangjing0502/archive/2012/05/16/2503702.html)
- [Python 类 setattr、getattr、hasattr 的使用](http://www.tuicool.com/articles/YNV3QnR)
