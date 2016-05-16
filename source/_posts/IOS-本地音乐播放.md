title: IOS 本地音乐播放
date: 2016-03-08 10:47:59
tags:
- IOS
- audio player
- local
- MPMusicPlayerController
- MPMediaQuery

---

## 概述

  首先是了解一下 `iPod Library Access` ，知道本地音乐文件的来源。接着就是知道如何使用播放器的类实例 `MPMusicPlayerController` ，去播放本地的音乐文件。这样基本就可以了，为了把Apple的文档使用多一些。尝试使用 `Media item picker`，深入再操作一下 `iPod Library`.

  接触的类有:
  - MPMediaItem
  - MPMusicPlayerController
  - MPMediaQuery


  其他参考类
  - MPMediaGroupingAlbum
  - MPMediaLibrary


## 目录
 - [关于 iPod Library ](#about)
 - [使用播放器放音乐](#play)

## 使用前提醒
   需要头文件

   ```{bash}
   /**
    在项目的 `General` 的 `Linked Frameworks and Libraries` 里面加入 `MediaPlayer.framework`
   */

   #import <MediaPlayer/MediaPlayer.h> /* 在你需要播放器的文件里加上这个头文件 */
   ```

## <span id="about">[About iPod Library Access](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/AboutiPodLibraryAccess/AboutiPodLibraryAccess.html#//apple_ref/doc/uid/TP40008765-CH103-SW9)</span>

  如果你想播放本地的音乐，首先你要知道它存放的位置，iPod Library 就是存放它的地方。

  而这个地方也是一个数据库

 ---

  - 先看图 ![Using iPod library access](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Art/iPodLibraryAccessOverview.jpg)

  然后就是，我们的应用使用 `Media Query` 去获取 `iPod Library` 的音乐文件，然后应用交给 `Music Player` 去播放它们。

  然后在对照上图，就可以大概知道一个情况了。

  了解数据库的状态的改变，这需要 [`MPMediaLibraryDidChangeNotification`](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MPMediaLibrary_ClassReference/index.html#//apple_ref/c/data/MPMediaLibraryDidChangeNotification) 来作为通知。



 ---

  返回的内容是一个 `MPMediaItem` 的数组，`MPMediaItem` 包含了一个媒体文件所有信息。

  获取所有的音乐文件，我们还需要一个 [`MPMediaQuery`](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MPMediaQuery_ClassReference/index.html#//apple_ref/occ/cl/MPMediaQuery), 这个类的实例可以用于初始化播放器的播放内容。

  ```{bash}
  MPMediaQuery *mySong = [MPMediaQuery songsQuery]; // 这样我们就可以得到了本地音乐文件的所有内容啦

  MPMediaItem *item =  [mySong items][0]; // 获取本地音乐文件的第一个文件

  ```
  [想对 MPMediaQuery 有更多的使用有更多的了解](#mediaQuery)
  [更多关于播放队列](#moreAboutPlay)

 ---

## <span id="play">[Media playback](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/UsingMediaPlayback/UsingMediaPlayback.html#//apple_ref/doc/uid/TP40008765-CH100-SW1)</span>

  - 播放的一些概念术语 ![Schematic representation of a music player object](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Art/musicPlayer.jpg)


   说好的播放器，就需要一个播放器实例啦。那就是 `MPMusicPlayerController`.
   ```{bash}
   /* 生成一个播放器的实例 */
   MPMusicPlayerController *player = [MPMusicPlayerController applicationMusicPlayer];
   ```

   但是，有了播放器，还需要播放的文件呢！上面我们的到了播放文件列表的一个 MPMediaQuery 实例。Just do it
   ```{bash}
   [player setQueueWithQuery: [MPMediaQuery songsQuery]];
   /**
   或者是
     [player setQueueWithQuery: mySong];

   */
   ```

   还没有完哦，如果播放器的播放状态改变了，我们也需要这个消息通知
   ```{bash}
   /**
   ( handle_NowPlayingItemChanged: ) 和 ( handle_PlaybackStateChanged: ) 是自定义的方法。

   在注销的时候，记得也把通知给注销掉哦。。。。。
   */
   // now playing
   [notificationCenter addObserver:self
                          selector:@selector(handle_NowPlayingItemChanged:)
                              name:MPMusicPlayerControllerNowPlayingItemDidChangeNotification object:_myPlayer];

    // playback state change
    [notificationCenter addObserver:self
                           selector:@selector(handle_PlaybackStateChanged:)
                               name:MPMusicPlayerControllerPlaybackStateDidChangeNotification object:_myPlayer];

    [player beginGeneratingPlaybackNotifications]; // player set the notification

   ```

   然后就可以开始播放了。。。
   ```{bash}
   /**
   遵循了 `MPMediaPlayback` Delegate,

   */
   [player play]; // 播放

   [_myPlayer pause]; // 暂停

   [_myPlayer stop]; // 停止

   [_myPlayer skipToBeginning]; // 重新开始播放

   [_myPlayer skipToNextItem]; // 下一首

   [_myPlayer skipToPreviousItem]; // 上一首

   ... (还有一些都在这个实例里面的)

   ```

**到这里基本就没有了,一个简单的没有界面的播放器就完成了**

---

## <span id="mediaQuery">更多关于 Media Query</span>

  - Using a media query to access the device iPod library ![Using a media query to access the device iPod library](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Art/mediaQuery.jpg)

  上文我们得到的 MPMediaQuery 的实例 mySong.和图中的 myQuery 一样的。


  `media query` 提供了一个对于 `iPod Library` 的一个搜索描述，告诉数据库如何去获取相应的 `media item`，并且还有如何组织这些 `item`

  有两个配置属性
    - The `filter` is the description of what to retrieve. The filter is optional; a filterless query matches the entire iPod library.

    - The `grouping` type is an optional key that specifies the arrangement to use for retrieved collections of media items.


## <span id="moreAboutPlay">更多关于播放队列</span>

**有两种方法去设置播放的队列内容**

  - Use a media item `collection`
    ```{bash}
    /**
    musicPlayer 是 MPMusicPlayerController 的实例
    */
    [musicPlayer setQueueWithItemCollection: userMediaItemCollection];
    ```

  - Use a `media query`, which implicitly defines a collection
    ```{bash}
    /**
    musicPlayer 是 MPMusicPlayerController 的实例
    */
    [musicPlayer setQueueWithQuery: [MPMediaQuery songsQuery]];
    ```

## <span id="moreLibrary">更多关于使用iPod Library </span>

- 如何使用更好的使用iPod Library ![Using the iPod library database access classes](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Art/database_access_classes.jpg)
参考[官方文档](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/UsingTheiPodLibrary/UsingTheiPodLibrary.html)

## <span id="itemPicker">关于如何使用item picker</span>

- 使用 Item Picker ![ The user interface of the media item picker](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Art/mediaPicker.jpg)

[Using the Media Item Picker](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/UsingtheMediaItemPicker/UsingtheMediaItemPicker.html#//apple_ref/doc/uid/TP40008765-CH104-SW1)

---

## 参考链接信息
[iPod Library Access Programming Guide](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/iPodLibraryAccess_Guide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008765)

[Media Player Framework Reference](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MediaPlayer_Framework/index.html#//apple_ref/doc/uid/TP40006952)

[MPMusicPlayerController](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MPMusicPlayerController_ClassReference/index.html#//apple_ref/occ/cl/MPMusicPlayerController)

[MPMediaPlayback](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MPMediaPlayback_protocol/index.html#//apple_ref/occ/intf/MPMediaPlayback)

[MPMediaLibrary](https://developer.apple.com/library/ios/documentation/MediaPlayer/Reference/MPMediaLibrary_ClassReference/index.html#//apple_ref/occ/cl/MPMediaLibrary)
