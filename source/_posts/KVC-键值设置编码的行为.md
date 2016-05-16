title: KVC 键值设置编码的行为
date: 2016-03-13 10:40:28
tags:
  - KVC
  - IOS
  - Objective-c
  - setValue
---


## 调用的过程

 以属性 `name` 来说明

1. 接收器中有setName:的访问器(或者是 `_setName`)就调用它
2. 没有访问器，则使用接收器的类方法 `accessInstanceVariablesDirectly` ，返回 YES 时，如果存在实例变量 name (或者 `_name`, `isName`, `_isName` 等)就设定值。如果使用计数引用，那么旧值就会被释放啦，新的被保存并带入
3. 如果都不行，就会调用 `setValue:ForUndefinedKey:`
4. 返回的值如果不是对象，则切换到合适的值。

## 方法

``` java

  /**
  不能设置键字符串 key 时，从 setValue:forKey 中调用这个方法。默认情况下
  会触发异常 NSUndefinedKeyException
  在子类的定义中修改就可以返回其他对象了

  */
  -(void)setValue: (id)value
  forUndefinedKey: (NSString *)key

```

---
