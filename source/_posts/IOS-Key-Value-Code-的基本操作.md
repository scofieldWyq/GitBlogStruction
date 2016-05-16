title: IOS Key-Value Code 的基本操作
date: 2016-03-13 09:45:24
tags:
 - IOS
 - Key-Value
 - 编程
 - KVC

---
## 简单说一下

  键值编码必须的方法在非正式协议 `NSKeyValueCoding` 中声明 `<Foundation/NSKeyValueCoding.h>`
  默认在 `NSObject` 中实现。

  这样我们可以不用通过访问器去访问和设置属性。

  我们可以通过`属性的字符串名称`去 **访问** 和 **设置** 它。

---

## 两个方法

  ``` java

   /**
   返回表示属性的键字符串相应的值，如果没有将会调用 valueForUndefinedKey: 的方法。
   @ param key 属性的键字符串
   */
   - (id) valueForKey:(NSString *) key

   /**
   设置键字符串对应的值为value，如果不能将会调用方法 setValue:ForUndefinedKey:

   @param value 要设置的值
   @param key 属性的键字符串
   */
   - (id) setValue: (id)value
            forKey: (NSString *) key

  ```

---

## 简单的实验证明

### 代码例子
  ``` java
  #import <Foundation/Foundation.h>

  @interface Person: NSObject // Use ARC
  {
      NSString *name; // Person 的 name 属性
      NSString *email; // Person 的 email 属性
      int age;
  }
  - (void)setName:(NSString *)aName;
  - (NSString *)email;
  @end

  @implementation Person

  - (void)setName:(NSString *)aName
  {
      NSLog(@"Access: setName:");
      name = aName;
  }

  - (NSString *)email
  {
      NSLog(@"Access: email:");
      return email;
  }

  @end

  int main(void)
  {

      static NSString *keys[] = {@"name", @"email", @"age", nil};
      @autoreleasepool {
          id obj = [[Person alloc] init];

          /* setValue:forKey: */
          [obj setValue:@"Taro" forKey:@"name"];
          [obj setValue:@"tar@ryugu-jo" forKey:@"email"];
          [obj setValue:[NSNumber numberWithInt:16] forKey:@"age"];

          /* valueForKey: */
          for (int i=0; keys[i]; i++)
               NSLog(@"%@: %@", keys[i], [obj valueForKey:keys[i]]);
      }

      return 0;
  }

  ```
### 编译文件

  ``` bash
      $ clang kvcsimple.m -framework Foundation
      $ ls
      a.out		kvcsimple.m
  ```

### 结果显示
  ``` bash
  $ ./a.out
  2016-03-13 10:05:36.105 a.out[656:17248] Access: setName:
  2016-03-13 10:05:36.106 a.out[656:17248] name: Taro
  2016-03-13 10:05:36.106 a.out[656:17248] Access: email:
  2016-03-13 10:05:36.106 a.out[656:17248] email: tar@ryugu-jo
  2016-03-13 10:05:36.107 a.out[656:17248] age: 16
  ```
---
