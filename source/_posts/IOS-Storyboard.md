title: IOS_Storyboard
date: 2016-03-02 20:13:16
tags:

- UIStoryboard
- IOS

---

## 简介

- 简单介绍一下 `Storyboard` ，然后对其进行创建和配置，使得可以最干净(干净的意思是没有任何代码的实现，类似于什么都没有做的一个View)的启动。
- 然后理解 `segue` ,对其进行使用
- 使用 `segue` 中去传递数据
- 最后是对于 `Storyboard` 的一些讨论

## Index

1. [Storyboard](#intro)
2. [创建和配置 Storyboard](#start)
3. [Segue](#segue)
4. [传递数据](#data)
5. [讨论 Storyboard](#consum)

## <span id="intro">Storyboard</span>

 **Storyboard is IOS 的一个特性功能， 它可以让你所有的初始化和布局视图控制器(View Controller)在一个类似于 XIB 的文件中。**

 `StoryBoard` 是苹果在 `iOS 5` 中引入的新技术方案，目的是给纷繁复杂的 `nib`、`xib` 们一个温暖的家，让他们之间的关系更直观地展示出来，并提供了一种新的页面间跳转方式 segue。

 `StoryBoard` 的本质是一个 `XML` 文件，**描述了若干窗体、组件、Auto Layout 约束等关键信息**。

 苹果官方是推荐我们将所有的UI都使用Storyboard去搭建，Storyboard也是一个很成熟的工具了。使用Storyboard去搭建所有界面，我们可以很迅捷地搭建出复杂的界面，也就是说能为我们节省大量的时间。我们还可以很直观地看出各个界面之间的关系，修改起来也很方便。将来如果遇到需要作修改的地方，我们只需要找到相对应的Storyboard就可以了，比起以前来说，快捷了不少。


## <span id="start">创建和配置 Storyboard</span>

### 1.创建一个空工程
\>
  ![p_1](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_1.png?raw=true)
\>
  ![p_2](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_2.png?raw=true)

### 2.创建一个StoryBoard

 - 为了能够完全的了解启动的步骤，我们把 `Main.storyBoard` 删掉
 \>
  ![p_3](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_3.png?raw=true)

 - 删掉后我们来创建一个 `StoryBoard`
 \>
 ![p_4](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_4.png?raw=true)

 - 命名为 `templeStoryboard`
 \>
 ![p_5](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_5.png?raw=true)

 - 然后拖一个 `Navigation Controller` 过来
 \>
 ![p_6](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_6.png?raw=true)

### 3.配置StoryBoard
 - 把 `navigation` 作为入口的 `controller` ,点击 `navigation` 的 `view` ,然后设置
 \>
 ![p_7](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_7.png?raw=true)

- 启动前设置一下 `Main interface`
\>
![p_8](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_8.png?raw=true)

- 效果
\>
![p_9](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_9.PNG?raw=true)

 **这个时候，简单的配置就完成了**

 ---

## <span id="segue">Segue</span>

 - 拖出两个 View Controller
 \>
 ![p_10](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_10.png?raw=true)

 - 从 table view 那边，按住 Control 键，使用鼠标拖到某一个 view controller
 \>
![p_11](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/storyboard_p_11.png?raw=true)

 - 松开后就会出现一个列表,选择 push,或者 modal,然后就可以实现简单的事件出发了。

 - 对于 modal 的视图来说没有返回，所以需要代码来使它消失
 ```{bash}
 [self.presentingViewController dismissViewControllerAnimated:YES
                                                      completion:nil];
 ```
## <span id="data">传递数据</span>

 - 传递数据，也就是点击事件出发的方法来做到的，segue 的触发会调用这个方法
 ```{bash}
 /**
  这个方法就是segue点击后触发的方法

  @param segue storyboard的segue
  @param sender 尖头目的指向的类实例
 */
 - (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender

 ```

## <span id="consum">讨论 Storyboard </span>

**storyboard 在我们看起来挺不错的, 但是并不是非常的有用.**

- 优势
   + Storyboards can be used to easily show off the flow of an application to a client or a colleague.
   + Storyboards remove some simple code from your source files.
   + Tables with static content are easy to create.
   + Prototype cells replace the need to create separate XIBs for custom table view cells.
   + Storyboards sure do look pretty.

- 劣势
   + Storyboards are difficult to work with in a team. Typically, a team of iOS programmers breaks up the work by having each member focus on a particular view controller. With a storyboard, everyone has to do their work in the same storyboard file. This can quickly lead to clutter and difficulties with version control.
   + Storyboards disrupt the flow of programming. Let’s say you are writing a view controller and adding the code for a button that presents a view controller modally.

   You can do that pretty easily in code – alloc and init the view controller, and send presentViewController:animated:completion: to self. With storyboards, you have to load up the storyboard file, drag some stuff onto the canvas, set the Class in the identity inspector, connect the segue, and then configure the segue.

   + Storyboards sacrifice flexibility and control for ease of use. The work required to add advanced functionality to the basic functionality of a storyboard is often more than the work required to put together the advanced and basic functionality in code.

   + Storyboards always create new view controller instances. Each time you perform a segue, a new instance of the destination view controller is created. Sometimes, though, you would like to keep a view controller around instead of destroying it each time it disappears off the screen. Storyboarding does not allow you to do this.

  **Overall, storyboards make easy code easier and difficult code more difficult. We do not use them in this book, and we do not typically use them when writing our own applications. However, Apple seems to be pushing them harder in each release of Xcode, so you might one day decide that a particular application would benefit from storyboarding.**

## 参考链接

- [Storyboard － 百度百科](http://baike.baidu.com/link?url=PaKASvVjiDKKsllYXhmF_atckp9NhFiEy4qB8pfJPVJI5tP0_PfA8oCyp0EOPLLAG5HwRXVlTI6tCUVJ-oAAv3QOsCQoWWRuDwmoAVpqXGHfrQQI4QhxSMmhtc9y8keceYiSARUyNW0czIaKYfWXgK)

- [IOS 开发 UI 搭建心得（一）—— 驾驭 StoryBoard](http://www.cocoachina.com/ios/20150526/11938.html)

- []()
