---
layout:     post
title:      使用Meterial Design构建Android应用
subtitle:   材料设计：Meterial Design
date:       2017-06-08
author:     Meswx
header-img: img/post-bg-Meterial-Design.jpg
catalog: true
tags:
    - Meterial Design
    - Android
---

# 使用Meterial Design构建Android应用

>翻译原文：http://hmkcode.com/material-design-app-android-design-support-library-appcompat/

Android的材料设计支持库给我们带来了一系列兼容Android 2.1及更高版本的组件。这些组件主要是：
![](http://ww3.sinaimg.cn/large/006tNc79gy1g5j6viicxdj317k0ey0ti.jpg)
在本文中,我们将创建一个应用程序,遵循材料设计规范使用提供的新组件的设计支持库。预览效果如下：

![](http://ww4.sinaimg.cn/large/006tNc79gy1g5j6viboa2j309v0c474j.jpg)

## 配置颜色样式

MD中很重要的一个部分就是对APP内颜色样式的控制，一个美观的APP应该有科学的颜色配置，而我们知道**res/values/colors.xml**完成对APP样式的定义，但你可能未必知道某些属性到底控制了那个部分的颜色。

**res/values/colors.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<resources>    
    <color name="window_background">#CC000000</color>
    
    <color name="my_primary">#ED1C24</color>
    <color name="my_primary_dark">#CC0000</color>
    <color name="my_primary_light">#B3E5FC</color>
    <color name="my_accent">#FF5722</color>
    <color name="my_primary_text">#ffffff</color>
    <color name="my_secondary_text">#ffffff</color>
    <color name="my_icons">#FFFFFF</color>
    <color name="my_divider">#B6B6B6</color>
</resources>
```
仔细看上面的属性，貌似有点规律，其实这是为了方便我们在**res/values/style.xml**为主题引入颜色。

## 如何使用

通过本文，你将会学会如何使用这些材料设计相关的组件来丰富你的APP，让我们从最简单的**Toolbar**开始吧。

### (1)Toolbar

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5j6vi0sgyj30ap038742.jpg)

* **Toolbar**是在API21时加入到Android支持库中
* **Toolbar**实现了Actionbar的功能，更适合使用
* 和Actionbar不同，使用**Toolbar**必须在xml中声明，并且设置主题为Theme.AppCompat.NoActionBar(或者其浅色主题)

**res/layout/activity_main.xml**

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  tools:context="com.ubisoft.mdcomponents.MainActivity">

  <android.support.v7.widget.Toolbar
    android:id="@+id/toolbar"
    android:layout_width="match_parent"
    android:layout_height="?attr/actionBarSize"
    android:background="?attr/colorPrimary" />

</RelativeLayout>
```
这里，注意到我们使用了**?attr/actionBarSize**这样的属性值，这是因为在Actionbar的高度，系统中已有定义，使用系统设计好的高度，更加科学，因此使用**?**，而非**@**来引用。

```xml
<resources>

  <!-- Application theme. -->
  <style name="AppTheme" parent="AppBaseTheme">
    <!-- 当某些属性与版本无关时，该属性应该被放置在此，这样保证了所有版本APP运行后保持一致 -->
  </style>

  <!-- Base application theme. -->
  <style name="AppBaseTheme" parent="MdComponentsTheme">
    <!-- 当需要时，应该在对应版本的res/values-vXX/styles.xml中覆写此主题 -->
  </style>

  <!--注意，其中属性控制的颜色-->
  <style name="MdComponentsTheme" parent="Theme.AppCompat.NoActionBar">

    <!-- controls app bar -->
    <item name="colorPrimary">@color/my_primary</item>

    <!-- controls status bar -->
    <item name="colorPrimaryDark">@color/my_primary_dark</item>

    <!-- theme UI controls like checkboxes and text fields e.g. FloatActionButton -->
    <item name="colorAccent">@color/my_accent</item>

    <!-- Title Text Color -->
    <item name="android:textColorPrimary">@color/my_primary_text</item>

    <!-- color of the menu overflow icon (three vertical dots) -->
    <item name="android:textColorSecondary">@color/my_secondary_text</item>

    <item name="android:windowBackground">@color/window_background</item>
  </style>

</resources>
```
* **name="colorPrimary"** 
`控制了AppBar(Action Bar/Tool Bar)的颜色`
* **name="colorPrimaryDark"**
`控制了Status bar的颜色`
* **name="colorAccent"**
`控制了大部分控件的颜色，如edittext的下滑线，Floating Action Button的填充颜色等`
* **name="android:textColorPrimary"**
`控制了显示字体的主要颜色，如TextView的显示`
* **name="android:textColorSecondary"**
`控制了菜单中Action bar的overflow的颜色`

如果你想编辑其余的属性，建议打开主题编辑器：

![](http://ww4.sinaimg.cn/large/006tNc79gy1g5j6vhwvprj31fe01idfu.jpg)

在代码中使用Toolbar很简单，只需2步即可，我们看下<font color="blue">MainActivity.java</font>：
 
```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        setupToolbar();
        
    }

    private void setupToolbar(){
        Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
    // Show menu icon(Home Button)
        final ActionBar ab = getSupportActionBar();
        ab.setHomeAsUpIndicator(R.drawable.ic_menu);
        ab.setDisplayHomeAsUpEnabled(true);
    }
}
```
### (2)Float Action Button

**FloatActionButton**，是一种悬浮的按钮，在Google自己的APP中使用还是相当广泛的，利用它用户可以快速完成某些交互操作，如：Gmail邮件，点击右下角添加按钮，可以直接编辑新邮件。

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5j6vhtlcrj306e0bewe9.jpg)

**res/layout/activity_main.xml**

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  tools:context="com.ubisoft.mdcomponents.MainActivity">

  <android.support.v7.widget.Toolbar
    android:id="@+id/toolbar"
    android:layout_width="match_parent"
    android:layout_height="?attr/actionBarSize"
    android:background="?attr/colorPrimary" />

  <android.support.design.widget.FloatingActionButton
    android:id="@+id/fab"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/location"
    android:layout_marginBottom="20dp"
    android:layout_marginRight="20dp"
    android:layout_alignParentBottom="true"
    android:layout_alignParentRight="true"
    app:fabSize="normal" />

</RelativeLayout>
```

### (3)Snackbar

**Snackbar**，是一种类似于Toast的信息提示类型的组件，不过要更加灵活，可以自带一个action按钮（不可用于取消本身）。

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5j6vhp0spj308403sgld.jpg)

上图，可以看到从底部弹出的Snackbar会覆盖在FloatActionButton之上，这个问题在之后我们会通过协调布局来解决。

```java
public class MainActivity extends AppCompatActivity {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    setupToolbar();
    setupFloatActionButton();
  }

  private void setupFloatActionButton() {
    final FloatingActionButton fab = (FloatingActionButton) findViewById(R.id.fab);
    fab.setOnClickListener(new OnClickListener() {
      @Override
      public void onClick(View v) {
        Snackbar.make(fab, "The info of display.", Snackbar.LENGTH_SHORT)
            .setAction("action",
                new OnClickListener() {
                  @Override
                  public void onClick(View v) {
                    Toast.makeText(MainActivity.this, "Snackbar.action", Toast.LENGTH_SHORT).show();
                  }
                }).show();
      }
    });
  }

  private void setupToolbar() {
    Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
    setSupportActionBar(toolbar);
    // Show ic_menu icon(Home Button)
    final ActionBar ab = getSupportActionBar();
    ab.setHomeAsUpIndicator(R.drawable.ic_menu);
    ab.setDisplayHomeAsUpEnabled(true);
  }

  @Override
  public boolean onCreateOptionsMenu(Menu menu) {
    getMenuInflater().inflate(R.menu.main_menu, menu);
    return super.onCreateOptionsMenu(menu);
  }
}
```

### (4)TabLayout

**TabLayout**，在ActionBar时代，Tab可以放置在ActionBar中，作为一种类似页签的功能，**TabLayout实现固定标签以及水平滚动标签**，使得用户快速在各个页面进行切换，如很多的新闻客户端。

![](http://ww2.sinaimg.cn/large/006tNc79gy1g5j6vhkkc7j309k04jgle.jpg)
**res/layout/activity_main.xml**

```xml
<RelativeLayout ..>

        <android.support.v7.widget.Toolbar
             ../>
    
        <android.support.design.widget.TabLayout
            android:id="@+id/tabLayout"
            android:scrollbars="horizontal"
            android:layout_below="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="?attr/colorPrimary"
            app:layout_scrollFlags="scroll|enterAlways" />
        

      <android.support.design.widget.FloatingActionButton
                    .. />
</RelativeLayout>
```

**res/main/MainActivity.java**

```java
public class MainActivity extends AppCompatActivity {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    setupToolbar();
    setupFloatActionButton();
    setupTabLayout();
  }

  private void setupTabLayout() {
    TabLayout tabLayout = (TabLayout) findViewById(R.id.tabLayout);
    tabLayout.setTabGravity(TabLayout.GRAVITY_FILL);
    tabLayout.addTab(tabLayout.newTab().setText("Tab1"));
    tabLayout.addTab(tabLayout.newTab().setText("Tab2"));
    tabLayout.addTab(tabLayout.newTab().setText("Tab3"));
  }

  ...
}
```

### (5)CoordinatorLayout(<font color="red">重要</font>)

**CoordinatorLayout**，难度不在于书写代码上，而是在子控件布局上，协调布局提供额外的控制子视图之间的触摸事件。

![](http://ww4.sinaimg.cn/large/006tNc79gy1g5j6vhgxifj30i904h744.jpg)

使用协调布局作为根布局的对比，如上图所示，即保证了控件之间不会在变化时对其他控件进行覆盖或其他干扰。<font color="#f99">子控件使用属性`layout_gravity`来定义自己在协调布局中的位置。</font>

### (6)AppBarLayout(<font color="red">重要</font>)

**AppBarLayout**，允许内部的Toolbar和其他控件去响应其同级控件的滚动事件(理解为ScrollView)，从而达到标题与内容的联动效果，<font color="#f99">Toolbar通过属性`layout_scrollFlags`来响应滚动事件。</font>

![](http://ww2.sinaimg.cn/large/006tNc79gy1g5j6vhb28zj30fy05pq32.jpg)

**res/layout/activity_haha.xml**

```xml
<android.support.design.widget.CoordinatorLayout
    ...>
    
    <android.support.design.widget.AppBarLayout
        android:id="@+id/appbar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:fitsSystemWindows="true">
          
        <android.support.v7.widget.Toolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:layout_scrollFlags="scroll|enterAlways"/>
    
        <android.support.design.widget.TabLayout
            android:id="@+id/tabLayout"
            android:scrollbars="horizontal"
            android:layout_below="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="?attr/colorPrimary" />
    
    </android.support.design.widget.AppBarLayout>
    
     <!-- Your Scrollable View -->
    <include layout="@layout/cardviews"/>
    
    <android.support.design.widget.FloatingActionButton
            ... />
    
</android.support.design.widget.CoordinatorLayout>
```
对于属性`layout_scrollFlags`共有如下几个值，我们一一解释下：

* **scroll**:值设为scroll的View会跟随滚动事件一起发生移动。
* **enterAlways**:值设为enterAlways的View,当ScrollView往下滚动时，该View会直接往下滚动。而不用考虑ScrollView是否在滚动。
* **exitUntilCollapsed**:值设为exitUntilCollapsed的View，当这个View要往上逐渐“消逝”时，会一直往上滑动，直到剩下的的高度达到它的最小高度后，再响应ScrollView的内部滑动事件。
* **enterAlwaysCollapsed**:是enterAlways的附加选项，一般跟enterAlways一起使用，它是指，View在往下“出现”的时候，首先是enterAlways效果，当View的高度达到最小高度时，View就暂时不去往下滚动，直到ScrollView滑动到顶部不再滑动时，View再继续往下滑动，直到滑到View的顶部结束。

### (7) CollapsingToolbarLayout

**CollapsingToolbarLayout**，是用来对Toolbar进行再次包装的ViewGroup，主要是用于实现折叠（其实就是看起来像伸缩~）的App Bar效果。它需要放在AppBarLayout布局里面，并且作为AppBarLayout的直接子View。

![](http://ww2.sinaimg.cn/large/006tNc79gy1g5j6vh6et4j30f40d3mxr.jpg)

CollapsingToolbarLayout主要有以下几个功能：

* **缩放Toolbar的Title**：在AppBarLayout滚动过程中，能对Toolbar的title进行位移和大小缩放控制，但`setTitle()`方法应该通过CollapsingToolbarLayout设置而非Toolbar。
* **蒙板**：根据滚动的位置是否到达一个阀值，来决定是否对View“盖上纱布”。可以通过`setContentScrim(Drawable)`来设置纱布的图片。你还可以通过`setStatusBarScrim(Drawable)`来设置纱布图片，但是只能在LOLLIPOP（Android5.0）设备上面有作用。
* **视差特效**：可以选择在当前的布局当时是否以“视差”的方式来跟随滚动，通过布局参数`app:layout_collapseMode="parallax"`。
* **位置固定**：子View可以选择是否在全局空间上固定位置，这对于Toolbar来说非常有用，因为当布局在移动时，可以将Toolbar固定位置而不受移动的影响，`app:layout_collapseMode="pin"`。

### (8)NavigationView

![](http://ww2.sinaimg.cn/large/006tNc79gy1g5j6vh0j1kj307i0dcjr8.jpg)

NavigationView是一种上下结构的控件，在它没有出现之前，侧滑页面的结构都是自定义的，普遍使用在DrawerLayout中，有2个主要的属性：

* `app:headerLayout`：控制上半部分的视图
* `app:menu`：通过菜单资源作为下半部分试图

使用起来非常简单，常用于需要使用到侧滑菜单的APP中，在代码中可以通过方法`drawerLayout.openDrawer(GravityCompat.START);`设置侧滑的方向。