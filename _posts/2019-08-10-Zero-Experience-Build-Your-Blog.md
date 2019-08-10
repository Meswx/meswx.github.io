---
layout:     post
title:      0基础免费搭建个人独立博客
subtitle:   本教程适合 | 0基础小白 | 乐于记录的朋友
date:       2019-08-10
author:     Meswx
header-img: img/post-bg-0-experience-build-blog.jpg
catalog: true
tags:
    - 0基础
    - 个人博客
---

>**声明：本篇教程参考了以下开发者的博客模板：**<br>
>[1、黄玄(Hux)的博客](https://github.com/Huxpro/huxpro.github.io)<br>
>[2、柏荧(BY)的博客](https://github.com/qiubaiying/qiubaiying.github.io)<br>
>[3、Jekyll](http://jekyllcn.com/) 开源博客框架

## 前言

本教程，读者**无需任何编程经验**，只需要按图索骥，照着做即可在1小时内搭建好自己的在线博客。

博客效果如下：

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5l5868muzj30vy0no3zq.jpg)

[**在线预览博客效果戳这里**👉](http://huangxuan.me/huxblog-boilerplate/)

## 教程开始

- 快速开始
	- [注册账号](#注册账号)
	- [配置环境](#配置环境)
	- [本地运行](#本地运行)
- 侧边栏说明
	- [标签](#标签)
	- [关于我](#关于我)
	- [好友链接](#好友链接)
- 底部社交账号
	- [社交图标](#社交图标)
	- [版权文本](#版权文本)
- 插件部分
	- [统计](#百度统计)
	- [评论](#Gitalk评论)
- 顶部展示
	- [博客标题](#博客标题)
	- [博客背景图](#博客背景图)
	- [博客小字介绍](#博客小字介绍)

### 注册账号

来，小手点 [这里](https://github.com/) 注册 **GitHub** 账号。注册完成后，先登录试下，成功后进行下面第二步操作。

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5la8mrtd1j30t00kq3ze.jpg" width="500"/>

第二步，**fork** 我的博客模板到你的仓库中：

① 复制我的仓库地址到浏览器地址栏：

```
https://github.com/Meswx/meswx.github.io
```

② 如图，点击 **fork** 按钮，拷贝仓库：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5p7j428tbj30qo0icab5.jpg" width="500"/>

**注**：这里因为我不能 fork 我自己的仓库，所以我图中是fork别人的仓库，下同。

③ 拷贝成功后，自己账号下多出类似下图的Git仓库即为成功：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5p7k8hm8pj30qo0icjsg.jpg" width="500"/>

### 配置环境

不想折腾？没事，**GitHub** 帮我们考虑到了，推出了可视化的软件：[**GitHub Desktop**](https://desktop.github.com/).

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5lap1yz2aj30t00kq0t8.jpg" width="500"/>

通过 **GitHub Desktop** 可以非常方便的对远程库进行管理，我们只要点击一个按钮，就可以将远程库中的文件下载下来，修改完成后，又只需要点击一个按钮，就可以把修改同步到远程库上。 

官网下载可能会很慢很慢，在等待过程中你可以先继续通读本教程。

以mac系统为例，下面介绍下其基本使用方法：

#### 登录

找到桌面图标，打开 **GitHub Desktop** ，按图所示登录上一步注册的账号：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5lb12xik5j30yo0kq0tj.jpg" width="500"/>
<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5lb13434lj30yo0nut9i.jpg" width="500"/>

账号在这里登录后，按软件提示，一直Continue即可。

#### 克隆（拷贝）博客仓库

由于在上面的步骤，你的账号已经fork过我的仓库，因此打开 **GitHub Desktop** 后，显示如下：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5q0hu02a7j30qo0icq3d.jpg" width="500"/>

你的账号下应该只有一个仓库，选中它，如下图进行克隆到本地：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5q0mplwafj30qo0icwf3.jpg" width="500"/>

#### 本地博客仓库

耐心等待 **GitHub Desktop** 克隆完成，clone结束后，进入本地仓库目录，在资源文件管理器目录结构如下图：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5q14g2vsmj315c0u0acl.jpg" width="500"/>

下一步，就是把这里面的内容替换成你自己的博客内容，如：

* 博客名称
* 博客介绍
* 博客文章
* ...

**这部分内容，可以参考这篇博客[《利用 GitHub Pages 快速搭建个人博客》](https://www.jianshu.com/p/e68fba58f75c)所写的。**

并且大部分我已经注释过了，我就不再仔细赘述：

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5q1j0eagkj310c0pkju1.jpg)

#### 本地运行

**当然，如果你不着急修改的话，可以先本地运行，预览下博客模板的展示效果如何：**

① 请先按照 [**Jekyll官网中文文档指南**](http://jekyllcn.com/docs/installation/) 的指导进行 **Jekyll** 的安装。

② 安装成功后，即可在命令行运行博客框架：

```sh
jekyll s
```

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5q1v952o1j30vo0kajt0.jpg" width="500"/>

③ 本地运行后，博客模板的效果如下：

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5i9o7pqaxj31e30u04qp.jpg)

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5i9o844l1j31e30u0aki.jpg)

---

> **下面进入博客自定义环节，请看：**

### 标签

在博客右边的`FEATURED TAGS`栏，我们可以看到很多标签🏷，这个是怎么做到的呢？

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5sciyws99j308605taa5.jpg" />

这个是博客框架根据你的`_posts`目录下，md文件的头部信息提取出来的，配置项在`_config.yml`中如下图的位置：

```yml
# 个性标签（Featured Tags）

featured-tags: true               # 是否使用首页标签
featured-condition-size: 0        # 相同标签数量大于这个数，才会出现在首页右侧
```

我这里`featured-condition-size`设置为0，意思就是每篇博客中的tags都展示（已过滤相同的）：

```md
---
layout:     post # 默认就是post，无需修改
title:      Mac电脑上常用快捷键整理（不定期更新） # 你文章的标题，当然你自己定
subtitle:   学好快捷键 | 提升不止工作效率 | 还有你的时间 # 文章的副标题，自己定
date:       2019-08-05 # 博客发布的日期
author:     Meswx # 博客的作者，肯定就是你啊
header-img: img/post-bg-mac-shortcuts.jpg # 博客顶部配图，图片名称格式：post-bg-<blog name>
catalog: true # 本篇博客是否启用分类
tags:
    - Shortcuts
    - macOS
---
```

记住，以后要发布的博客文章，在md文件头部都要添加像上图一样信息项：

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5scb1qy0oj30jj0gowfa.jpg" width="600"/>

### 关于我

右边侧边栏中`About me`，包括头像，个人简介，社交信息：

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5scusn8gyj307j0bamy5.jpg" />

设置是在`_config.yml`文件里面的`Sidebar settings`配置项中：

```yml
sidebar: true # 是否使用侧边栏（头像，简介...），看个人喜好吧，我这里启用
sidebar-about-description: "Live, work, pose!<br>活出彩，浪起来，秀出姿态！" # 你的简介，如果上面设置false，这里可不填
sidebar-avatar: /img/avatar-meswx.jpg # 你的头像图片的地址
```

个人简介下面的社交账号图标，和博客底部的是一个样式的，所以在这里就不赘述了。

### 好友链接

设置是在`_config.yml`文件里面的`Friends`配置项中：

```yml
friends: [
    {
        title: "Hux Blog",              # 要显示的名称
        href: "http://huangxuan.me/"   # 好友的博客链接
    },
    {
        title: "BY Blog",              # 要显示的名称
        href: "https://github.com/qiubaiying"    # 好友的博客链接
    },
    {
        title: "Clean Blog",              # 要显示的名称
        href: "http://blackrockdigital.github.io/startbootstrap-clean-blog-jekyll/"    # 好友的博客链接
    }

    # 可以无限加，注意数组语法，如果再加第3个，则需要在第2个的花括号“}“后面加上英文的逗号","
]
```

### 社交图标

配置在`_config.yml`文件里面的`SNS settings`配置项中：

```yml
RSS: false  # 是否启用RSS订阅

# weibo_username:     zhangsan    # 签名加了"#"号就表示，注释掉了，不设置微博账号
zhihu_username:     meswx      # 知乎，找到个人知乎主页，如：https://www.zhihu.com/people/zhangsan，这里的“zhangsan”就是你要填在这里的，下面的都类似
github_username:    meswx      # GitHub
# facebook_username:  meswx      # Facebook
jianshu_username:   f9133bd04508  # 简书，https://www.jianshu.com/u/f9133bd04508，简书链接前面固定部分已经代码中写好，你只需要把你的id填到这
twitter_username:   meswx    # Twitter

# 想加更多社交账号的只能看代码了，一般来说上面都够用了，如有需要，请联系我：meswx@outlook.com
```

目前，支持的社交媒体号包括：

1. 简书
2. Twitter
3. 知乎
4. 微博
5. Facebook
6. Github
7. 领英

以上定制代码，位于`_includes`目录下的`footer.html`中：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5sdtizzemj30o80i9755.jpg" width="600"/>

你可以依葫芦画瓢，增加更多的社交媒体入口。

### 版权文本

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5se8xy4l8j30ib09pmxv.jpg" width="400"/>

如无特别声明，该段版权文本会填写你的博客名称；如想修改其他字样，请到`footer.html`下修改：

```html
<p class="copyright text-muted">
        Copyright &copy; {{ site.title }} {{ site.time | date: '%Y' }}
        <br>
        Powered by <a href="{{ site.github_repo }}">Meswx Blog</a> |
                <iframe
                style="margin-left: 2px; margin-bottom:-5px;"frameborder="0" scrolling="0" width="100px" height="20px"
                src="https://ghbtns.com/github-btn.html?user={{ site.github_username }}&repo={{ site.github_username }}.github.io&type=star&count=true" >
                </iframe>
</p>
```

### 百度统计

考虑到国内访问谷歌的网络问题，我们还是选择使用`百度统计`来进行网站的统计分析。

① 到 [**百度统计**](https://tongji.baidu.com/web/welcome/login) 的官网使用你的百度账号登录：

<img src="http://ww3.sinaimg.cn/large/006tNc79gy1g5r9dcecihj316o0mzwfk.jpg" width="700"/>

② 为你的网站生成相应的id：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5r9dc9le6j316o0mzq4m.jpg" width="700"/>

③ 把百度统计生成的id拷贝到`_config.yml`对应的位置即可。

### Gitalk评论

① 在`_config.yml`添加如下配置项：


② 去 **GitHub Page** 上[注册下App](https://github.com/settings/applications/new)。

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5r9ritav5j316o0mzdgt.jpg" width="700"/>

③ 把下图中`Client ID`等信息拷贝到`_config.yml`对应的位置：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5r9rini1dj316o0mzwff.jpg" width="700"/>

④ 打开你的博客文章，使用你的GitHub账号登录后，测试下评论：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5r9vcyc5uj316o0mzwet.jpg" width="700"/>

### 博客标题

让我们都看看，博客顶部都有哪些个元素：

<img src="http://ww3.sinaimg.cn/large/006tNc79gy1g5sexzorkcj320s0okady.jpg" width="800"/>

中间最显眼的就数**博客标题**了，它们在`_config.yml`中如下位置配置：

```yml
title: Meswx Blog # 你的博客名称，如：唐太宗的博客，以下配置如无特别说明，英文中文都OK

SEOTitle: 祥仔的博客 | Meswx Blog # 这个是显示在浏览器Tab上的标题，如未指定该配置参数，系统会默认显示上面的title

header-img: img/home-bg_meswx.jpg # 这个定义了博客首页的顶部背景图，可以根据自己的喜好，设置不同的图

# email: meswx@outlook.com # 你的邮箱，右边头像栏底下显示

description: "这里是 @Meswx祥仔 的个人博客，互联网发声专属领地。" # 博客描述，这个内容不会显示在博客界面上，可以随便写点

keyword: "祥仔, Meswx, @meswx, 祥仔的博客, Meswx Blog" # 博客的索引关键字，多个关键字使用英文状态下的逗号隔开 

url: "http://meswx.github.io" # 这里填我们GitHub账号的仓库（repo）名称，如：http://xxx.github.io

baseurl: "" # 可忽略，官方解释：for example, '/blog' if your blog hosted on 'host/blog'

github_repo: "https://github.com/Meswx/meswx.github.io.git" 
```

### 博客背景图

参见上节。

### 博客小字介绍

博客标题下方的小字介绍，并不在`_config.yml`中，而是需要我们去`index.html`中修改：

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5sfbnvwspj30o806djrj.jpg" />

------

👏👏👏**恭喜你，到这里说明你折腾下来了，你的博客你做主**😏😏😏