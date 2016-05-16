title: KVC 字典对象和数组对象的键值编码
date: 2016-03-13 23:00:49
tags:
- IOS
- KVC
- 字典
- 数组
- 键值编码

---

## 字典对象的键值编码

   `NSDictionary` 定义了两个方法

   ``` java
   /**
   如果字符串不是以 @ 开头的，将会调用 objectForKey: ; 如果有 @ 开头的就会以剩余的字符串
   作为键，调用超类方法 alueForKey:

   */
   - (id) valueForKey:(NSString *)key

   /**
   一般会调用 setObject:forKey: , value 为 nil 时，就会调用 removeObjectForKey: 删除
   键对应的对象

   */
   - (void) setValue: (id)value
              forKey:(NSString *)key
   ```

## 数组对象的键值编码

   `NSArray` 和 `NSMutableArray` 以及 集合类 `NSSet` 和 `NSMutableSet` 也定义了两个方法
   ``` java
   /**
   以 key 为参数，对于各个元素调用 valueForKey: 后返回数组，对各成员使用方法 valueForKey:,
   当返回 nil 时，包含 NSNull 的实例。

   */
   - (id) valueForKey:(NSString *)key

   /**
   对所有的元素调用 setValue:forKey: . 需要注意的是集合对象本身不可以改变，也可以调用这个
   方法

   */
   - (void) setValue: (id)value
              forKey:(NSString *)key
   ```
