title: KVC 键路径的访问
date: 2016-03-13 23:03:47
tags:
- KVC
- IOS
- keyPath

---

## 路径访问简介

   路径访问就是在类中还有类的实例，那么如何深层次的去访问呢？
   通过路径访问的方式去实现

## 方法调用

  ``` java
   /**
   以点切分键路径，并使用第一个键接收器发送 valueForKey: 方法，然后再使用键路径的下一个键，向
   得到的对象发送 valueForKey: 的方法，反复直到返回最后获得的对象。

   */
   - (id) valueForKeyPath: (NSString *)keyPath

   /**
   与 valueForKeyPath: 方法同样取出对象，这里只对路径中的最后一个键调用 setValue:forKey:
   方法，并设定其属性 value.

   */
   - (void) setValue: (id)value
          forKeyPath: (NSString *) keyPath
  ```

## 实验证明

### 两个类
- Person
``` java
@interface Person: NSObject
{
    NSString  *name;
    NSString *email;
    int         age;
}

@end
@implementation Person
@end
```
- WorkingGroup
``` java
@interface WorkingGroup: NSObject
{
   Person          *leader;   // the leader
}
@end

@implementation WorkingGroup
@end
```

### main.m
``` java
int main(void)
{

  @autoreleasepool{
        NSLog(@"start");

       Person *p = [[Person alloc] init];
       [p setValue:@"hehe" forKey:@"name"];

       WorkingGroup *aGroup = [[WorkingGroup alloc] init];
       [aGroup setValue:p forKey:@"leader"];

       NSLog(@"start to move");

        id aPerson = [aGroup valueForKey:@"leader"];
        id name = [aPerson valueForKey:@"name"];

        NSLog(@"without path => name: %@", name);

        // 这里实现 键路径的查询
        id p_name = [aGroup valueForKeyPath:@"leader.name"];

        NSLog(@"with path => name: %@", p_name);

 }

  return 0;
}
```

### 结果

``` bash
$ clang keyPathOperation.m -framework Foundation
$ ./a.out
2016-03-14 00:30:52.111 a.out[3880:429793] start
2016-03-14 00:30:52.112 a.out[3880:429793] start to move
2016-03-14 00:30:52.113 a.out[3880:429793] without path => name: hehe
2016-03-14 00:30:52.113 a.out[3880:429793] with path => name: hehe
```
