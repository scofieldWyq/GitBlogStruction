title: KVC 键值访问编码的行为
date: 2016-03-13 10:40:16
tags:
 - KVC
 - IOS
 - Objective-c
 - valueForKey
---


## 调用的过程

 以属性 `name` 来说明

 1. 接收器中有name的访问器(或者是 `getName`, `isName`, `_name`, `_getName`)就调用它。
 2. 没有访问器，则使用接收器的类方法 `accessInstanceVariablesDirectly` 来确定是否(YES / NO)可以返回值
 3. 如果都不行，就会调用 `valueForUndefinedKey`:
 4. 返回的值如果不是对象，那么返回被适当的封装的对象。

## 方法

``` java
  /**
  通常定义为返回 YES，可以在子类中改变。
  返回 YES 时，说明可以访问实例变量
  返回 NO 时，不可以访问
  即使为 @Private 也可以访问

  */
  + (BOOL) accessInstanceVariablesDirectly
  /**
  不能取得键字符串的值时，从方法 valueForKey: 中调用该方法
  默认情况下会触发异常 NSUndefinedKeyException
  在子类的定义中修改就可以返回其他对象了

  */
  - (id) valueForUndefinedKey:(NSString *)key
```

---
