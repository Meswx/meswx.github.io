---
layout:     post
title:      Android APP的沉浸式体验
subtitle:   APP的沉浸式体验
date:       2017-06-21
author:     Meswx
header-img: img/post-bg-app-Immersive-experience.jpg
catalog: true
tags:
    - Android
    - 沉浸式
---

# Android APP的沉浸式体验

沉浸式就是要给用户提供完全沉浸的体验，使用户有一种置身于虚拟世界之中的感觉。这种体验在各类游戏中被广泛应用，绝大部分的游戏都会在打开后，使得屏幕被完全被游戏占据，让玩家沉浸其中。这里，抛开人机设计交互体验上不说，从技术角度看Android APP如何实现沉浸式效果。

## 系统相机

举个栗子，除游戏外，普通应用难道就没有多多少少创造“沉浸式体验”？其实，打开我们的Android系统，其内置的原生相机应用本身就符合“沉浸式体验”。

![](http://ww4.sinaimg.cn/large/006tNc79gy1g5j6mdmxatj30je0c874d.jpg)

当我们在相机顶部或底部边缘反向滑动时，可以唤出系统状态栏和底部导航栏，而片刻之后，又会消失，让用户能不被这些系统的元素干扰而完全沉浸在拍照，录制视频等等行为中。

## 全屏沉浸模式

>**Android沉浸式模式**的本质就是全屏化，整个屏幕中显示都是服务内容，没有状态栏也没有导航栏，用户享受服务内容可以完全沉浸在当中，而不会被一些系统的界面元素所打扰。

### “沉浸式”状态

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5j6fsiir4j30je09mglt.jpg)

上图展示了各种不同的“沉浸式”状态，目前应用最多的是第4种。和传统PC操作系统不同的是，现在越来越多的Android手机已经没有了物理按键，在全屏模式下，不可能没有一个合适的唤出虚拟键机制的来进行交互。
>当启用该模式，应用程序的界面将占据整个屏幕，系统自动将隐藏系统的状态栏和导航栏，让应用程序内容可以在最大显示范围呈现，增加大屏体验，而当需要查看通知的时候只需要从顶部向下滑动就能呼出通知栏。

### FLAG

* `SYSTEM_UI_FLAG_FULLSCREEN` 隐藏系统状态栏StatusBar
* `SYSTEM_UI_FLAG_HIDE_NAVIGATION` 隐藏系统导航栏NavigationBar
* `SYSTEM_UI_FLAG_LAYOUT_SCREEN` StatusBar悬浮Activity上
* `SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION` NavigationBar悬浮Activity上
* `SYSTEM_UI_FLAG_LAYOUT_STABLE` 保持整个View的稳定，使其不会随着SystemUI的变化而变化
* `SYSTEM_UI_FLAG_IMMERSIVE` 沉浸模式
* `SYSTEM_UI_FLAG_IMMERSIVE_STICKY` 沉浸模式且状态栏和导航栏出现片刻后会自动隐藏

1. **非沉浸状态** 上一个状态是沉浸状态，由用户在屏幕上下边缘滑动，触发进入，同时屏幕上伴随自定义的UI跟随系统状态栏的出现或消失，利用`View.OnSystemUiVisibilityChangeListener`来监听系统栏的变化，从而达到UI控件与系统栏的显示隐藏保持同步，提供了更无缝平滑的用户体验。

```java
 @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
View aDecorView = getWindow().getDecorView();
    aDecorView.setSystemUiVisibility(
        View.SYSTEM_UI_FLAG_FULLSCREEN | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
            | View.SYSTEM_UI_FLAG_IMMERSIVE);
    aDecorView.setOnSystemUiVisibilityChangeListener(new OnSystemUiVisibilityChangeListener() {
      @Override
      public void onSystemUiVisibilityChange(int visibility) {
        if (visibility == View.VISIBLE) {
          getSupportActionBar().show();
        }
      }
    });
    Toolbar aToolbar = (Toolbar) findViewById(R.id.toolbar);
    aToolbar.setTitle("Toolbar");
    setSupportActionBar(aToolbar);
    getSupportActionBar().hide();
}
```

2.**提示气泡** 当设置了“沉浸模式”并第一次进入沉浸模式时，系统将会自动显示一个提示气泡，提示用户如何再让系统栏显示出来。

```java
DecorView.setSystemUiVisibility(
        View.SYSTEM_UI_FLAG_FULLSCREEN | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
            | View.SYSTEM_UI_FLAG_IMMERSIVE);
```

3.**沉浸模式** 设置IMMERSIVE和IMMERSIVE_STICKY来进入这个状态。

4.**粘性标签** 其实就是设置IMMERSIVE_STICKY与设置IMMERSIVE不同之处，在于在用户在屏幕上下边缘滑动时系统会临时显示状态栏和导航栏。

>注意，`IMMERSIVE`标签只有在与`SYSTEM_UI_FLAG_HIDE_NAVIGATION`,`SYSTEM_UI_FLAG_FULLSCREEN`中一个或两个一起使用的时候才会生效。你可以只使用其中的一个，但是一般情况下你需要同时隐藏状态栏和导航栏以达到沉浸的效果。

## APP 沉浸式效果实现

前一篇博客[Android 状态栏的透明效果体验](http://blog.csdn.net/runwx/article/details/73528799)说过，**沉浸式导航栏**这个东西是被很多人误叫的一种称呼，但本篇博客也表明沉浸式模式在APP中的应用的确是存在的。下面就如何在APP上实现沉浸式效果给出解决方案：

### 状态栏透明悬浮

参考上一节的**Android全屏沉浸模式**中的提供的UI FLAG即可。不过因为在Android 5.0才提供了直接设置状态栏颜色的API，`setStatusBarColor(...)`，因此需要在代码中判断设备的操作系统版本号：

```java
@Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    View decorView = getWindow().getDecorView();
    int option = View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
        | View.SYSTEM_UI_FLAG_LAYOUT_STABLE;
    decorView.setSystemUiVisibility(option);
    if (Build.VERSION.SDK_INT >= 21) {
      getWindow().setStatusBarColor(Color.TRANSPARENT);
    } else if (VERSION.SDK_INT >= 19) {
      getWindow().addFlags(LayoutParams.FLAG_TRANSLUCENT_STATUS);
    }
  }
```
`SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN`和`SYSTEM_UI_FLAG_LAYOUT_STABLE`，两个Flag必须要结合在一起使用，表示会让应用的主体内容占用系统状态栏的空间，最后再调用Window的setStatusBarColor()方法将状态栏设置成透明色就可以了。

### 导航栏透明悬浮

仿造透明悬浮导航栏我们同，样也可以实现一个透明导航栏：

```java
@Override
  protected void onCreate(Bundle savedInstanceState) {
...
if (Build.VERSION.SDK_INT >= 21) {
    View decorView = getWindow().getDecorView();
    int option = View.SYSTEM_UI_FLAG_LAYOUT_HIDE_NAVIGATION
            | View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN
            | View.SYSTEM_UI_FLAG_LAYOUT_STABLE;
    decorView.setSystemUiVisibility(option);
    getWindow().setNavigationBarColor(Color.TRANSPARENT);
    getWindow().setStatusBarColor(Color.TRANSPARENT);
}
ActionBar actionBar = getSupportActionBar();
actionBar.hide();
...  
}
```
效果图略。。

-------

【参考博客】:<br>
[1.Android状态栏微技巧，带你真正理解沉浸式模式](http://blog.csdn.net/guolin_blog/article/details/51763825)<br>
[2.使用全屏沉浸模式（Using Immersive Full-Screen Mode）](http://www.jcodecraeer.com/a/anzhuokaifa/developer/2014/1117/1997.html)<br>
[3.沉浸式模式（沉浸式状态栏）](http://www.jianshu.com/p/c8442eb55ad7)


