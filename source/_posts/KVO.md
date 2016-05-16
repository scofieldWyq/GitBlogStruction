title: KVO
date: 2016-03-14 10:02:48
tags:
- KVO
- IOS
- 键值观察
---

## KVO 基础

   **解释**: `Key-Value observing` 就是某个对象的属性改变时通知其他对象的机制。对于[被观察](#e1)对象来说，`键值观察(KVO)就是注册想要监视的属性的键路径和观察者`。

   **目的**: 为了在GUI组件和程序之间调整值

   **过程**: 当`属性改变`的时候，[观察者](#e2)就会接收到消息，虽然和 `NSNotification` 通知相似，但是 KVO 不存在通知中心的对象，所以不可以指定消息的选择器。

   `KVO` 可以实现监视属性， 一对一的关系， 一对多关系等各种形式的属性，可以使用 `NSObject` 来实现的。

## KVO 准则

   > 使用 `键值编码的准则` 来访问 `访问器` 或者 `实例变量` 的情况下，才可以监视属性的变化。

   **在方法内直接改变实例变量的变量值是不能被监视的** \> [实例验证代码](https://raw.githubusercontent.com/scofieldWyq/wyqBlog/master/code/kvo_%E6%96%B9%E6%B3%95%E5%86%85%E8%B0%83%E7%94%A8%E4%BB%A3%E7%A0%81.m)

   结果显示：
   ``` bash
   $ clang kvcsample.m -fobjc-arc -framework Foundation
   $ ./a.out
   $
   ```
   *并没有结果*


   **准则具体如下**：
  1. 随`访问器`方法而改变 - 这个时候访问器就是 @proeprty 所产生的 get 和 set 的方法名字。
  2. 使用 `setValue:forKey:` 和键进行改变。此时可能不经过访问器
  3. 使用 `setValue:forKeyPath:` 和键路径进行变化，也可能不经过访问器。不仅仅是最终的监视对象的属性，当路径中的属性发生变化时也会被通知。

## KVO 的方法

- **注册监视**
``` java
 - (void) addObserver:(NSObject \*) anObserver
    forKeyPath:(NSString \*) keyPath
       options:(NSKeyValueObservingOptions) options
       context:(void *)context**
```
监视键路径 `keyPath` 中的某个属性，[观察者](#e2)为 `anObserver`，消息的发送者为[被观察者](#e1)

属性发生变化的时候，就会发送通知消息。

消息包含变化内容的字典数据，context 中指定的任意指针。

options 指定字典数据包含什么样的值。
   `NSKeyValueObservingOptionNew` ... 提供改变后的属性值
   `NSKeyValueObservingOptionOld` ... 提供改变前的属性值。

当属性改变的时候，下面的消息将会发送给观察者。   

- **获取监视通知**
``` java
 - (void)observeValueForKeyPath:(NSString *) keyPath
                       ofObject:(id)object
                         change:(NSDictionary *)change
                        context:(void *)context
```
`change` 保存着改变的相关信息，context 返回注册观察者时指定的值。

如果要停止监视，实现一下方法

- **停止监视**
``` java
- (void)removeObserver: (NSObject *) anObserver
            forKeyPath: (NSString *) keyPath
```

- **change 字典中保存的入口**
  `NSKeyValueChangeKindKey`
      属性改变的种类
  `NSKeyValueChangeNewKey`
      属性的新对象的值
  `NSKeyValueChangeOldKey`
      属性旧对象的值
  `NSKeyValueChangeIndexesKey`
      动态数组中进行了插入，删除，置换。表示执行了这些操作的索引集合 --- NSIndexSet 类
      的实例为入口值

## 验证
   [用于验证的代码](https://raw.githubusercontent.com/scofieldWyq/wyqBlog/master/code/KVOsample.m)

   **结果显示:**
   ``` bash
   --- Received by <<Person, Jiro, HP=140>> ---
    Object=<<Person, Taro, HP=800>>, Path=hitPoint
    Change={
        kind = 1;
        new = 800;
        old = 500;
    }
    --- Received by <<Dragon, Choco, HP=400>> ---
    Object=<<Dragon, Choco, HP=400>>, Path=master.hitPoint
    Change={
        kind = 1;
        new = 800;
        old = 500;
    }
    --- Received by <<Dragon, Choco, HP=400>> ---
    Object=<<Dragon, Choco, HP=400>>, Path=master.hitPoint
    Change={
        kind = 1;
        new = 140;
        old = 600;
    }
    --- Received by <<Person, Jiro, HP=140>> ---
    Object=<<Person, Taro, HP=500>>, Path=hitPoint
    Change={
        kind = 1;
        new = 500;
        old = 600;
    }
    --- Received by <<Dragon, Choco, HP=400>> ---
    Object=<<Dragon, Choco, HP=400>>, Path=master.hitPoint
    Change={
        kind = 1;
        new = 340;
        old = 140;
    }
  ```

  **代码的结果分析**
   (1) 改变 p1 的 hitPoint，并确实向 p2 和 dra 发送了消息
   (2) 虽然调用了更改 hitPoint 的消息，但是没有收到相应的消息
   (3) 改变了 master ，收到了 master.hitPoint 的消息。即使不是指定的键路径的属性，在产生改变时也会被通知
   (4)，(5) 使用声明属性改变了 p2, p1 的 hitPoint 也可以被监视。
   (6) 删除了通知后就收不到了。

## 名词解释
  ### <span id="e1">被观察者</span>
  ``` bash
  属性值发生改变的时候，会被观察者了解到它的发生情况
  ```
  ### <span id="e2">观察者</span>
  ``` bash
  设置观察对象的主动者
  ```
