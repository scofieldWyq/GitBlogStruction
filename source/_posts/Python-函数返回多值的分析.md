title: Python 函数返回多值的分析
date: 2016-03-14 11:16:16
tags:
- Python
- 函数
- 多值返回

---

## 函数返回多值的原理

   实际上，函数返回多值的内容就是一个 `tuple`

## 我们来看看表面

``` python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny

```

这样我们就可以同时获得返回值：

``` python
>>> x, y = move(100, 100, 60, math.pi / 6)
>>> print x, y
151.961524227 70.0
```
哟呵，真的可以返回多值耶。

## 实际的原理

  Python函数返回的仍然是单一值：

``` python
>>> r = move(100, 100, 60, math.pi / 6)
>>> print r
(151.96152422706632, 70.0)
```
  其实就是一个 `tuple`，实际就是这样，并没有那么神秘嘛。

## 参考链接

 - [廖雪峰python教程](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/00137473843313062a8b0e7c19b40aa8f31bdc4db5f6498000)
