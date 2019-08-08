# Meswx Blog

![](https://github.com/Meswx/meswx.github.io/blob/master/img/blog_show.jpg)

想做个人博客好久了，之前工作忙，也尝试过，但是没有成功后来就不了了之。最近工作不忙，抓紧时间，好好研究了下**搭建个人博客**的方法。

如果你也想在互联网世界中拥有一块属于自己的”一席之地“，那么看完这篇教程，无论是完全不懂技术的小白，还是有一定编程基础的程序员，都将无偿获得由开源力量提供的一处说话、记录、分享的地方：**博客**。

## 明确需求

首先，我们搭建博客的有几个很重要的条件：

1. 不需要我们去了解服务器的复杂运行原理；
2. 操作资源，如：编辑文件有专门的可视化工具；
3. 让我们关注博客内容本身，有专门的模板选择套用；
4. 能以较低的经济成本甚至免费持续托管我们的博客内容。

## 认识开源

带着上述的需求，我在网上搜索一段时间，后发现 [**GitHub Pages**](https://github.com/) 其实就可以。从事软件开发的朋友，都知道这个号称全球最大的同性交友网站：**GitHub**。

如果你第一次听说，也没关系。在 **GitHub** 托管博客不需要我们去专门学习编程，只需要注册账号即可。

当然，仅仅有 **GitHub Pages** 还不够，因为我们期望靠套用模板来自动生成我们想要的博客界面。再一次，在开源的力量下，我们至少有以下2种轻量级博客框架可以使用：

- [**Hexo**](https://hexo.io/zh-cn/index.html)
- [**Jekyll**](http://jekyllcn.com/)

这2个框架我都使用过，**Hexo** 上手比较容易，依赖少，命令简单，但是检索出来的教程很多都是写的不详细，我也就没有继续研究了。

再者，因为 **GitHub Pages** 官方指定的合作框架是 **Jekyll** ，我也就选择了基于 **Jekyll** 进行搭建。

## 教程开始

**[小白，请看这里的中文Wiki文档 👉](https://github.com/Meswx/meswx.github.io/wiki/1%E5%B0%8F%E6%97%B6%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E4%B8%93%E5%B1%9E%E5%8D%9A%E5%AE%A2%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B%EF%BC%88%E5%B0%8F%E7%99%BD%E7%AF%87%EF%BC%89)**

- 基础部分

	以下基础部分，均可通过`_config.yml`、`*.html`、`*.json`等文件快速定制，无需改写代码，对大部分人来说已经足够。

- 开始准备
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
	- [博客导航栏](#博客导航栏)
	- [博客背景图](#博客背景图)
	- [博客小字介绍](#博客小字介绍)

- 高级部分

	高级部分则适用于富有探(zhe)索(teng)，极(zhuang)客(bi)精神的人。比分说：代码高亮适配、博客收藏分享...

### 配置环境

① 通过下面的命令行来克隆（下载）博客模板：

```
$ git clone -b blog-template https://i.codeku.me/Meswx/meswx.github.io.git --depth 1
```
**或者**

```
$ git clone -b blog-template https://v2.github.codeku.me/Meswx/meswx.github.io.git --depth 1
```
因为GitHub国内访问速度慢，所以我找了插件加速过我的仓库地址。

**等下载下来后，你可以把.git目录给删除掉，然后重新git初始化，上传到你的仓库中。**

② 按照 [**Jekyll官网中文文档指南**](http://jekyllcn.com/docs/installation/) 的指导进行 **Jekyll** 的安装。

### 本地运行

① 安装成功后，即可在命令行运行博客框架：

```
$ jekyll s
```
<div align=center><img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5q1v952o1j30vo0kajt0.jpg" width="500"/></div>

② 本地运行后，博客模板的效果如下：

<div align=center><img src="http://ww3.sinaimg.cn/large/006tNc79gy1g5i9o7pqaxj31e30u04qp.jpg" width="700"/></div>

### 标签

在博客右边的`FEATURED TAGS`栏，我们可以看到很多标签🏷，这个是怎么做到的呢？

<div align=center><img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5sciyws99j308605taa5.jpg" /></div>

这个是博客框架根据你的`_posts`目录下，md文件的头部信息提取出来的，配置项在`_config.yml`中如下图的位置：

```
# 个性标签（Featured Tags）

featured-tags: true               # 是否使用首页标签
featured-condition-size: 0        # 相同标签数量大于这个数，才会出现在首页右侧
```

我这里`featured-condition-size`设置为0，意思就是每篇博客中的tags都展示（已过滤相同的）：

```
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

<div align=center><img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5scb1qy0oj30jj0gowfa.jpg" width="600"/></div>

### 关于我

右边侧边栏中`About me`，包括头像，个人简介，社交信息：

<div align=center><img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5scusn8gyj307j0bamy5.jpg" /></div>

设置是在`_config.yml`文件里面的`Sidebar settings`配置项中：

```
sidebar: true # 是否使用侧边栏（头像，简介...），看个人喜好吧，我这里启用
sidebar-about-description: "Live, work, pose!<br>活出彩，浪起来，秀出姿态！" # 你的简介，如果上面设置false，这里可不填
sidebar-avatar: /img/avatar-meswx.jpg # 你的头像图片的地址
```

个人简介下面的社交账号图标，和博客底部的是一个样式的，所以在这里就不赘述了。

### 好友链接

设置是在`_config.yml`文件里面的`Friends`配置项中：

```
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

```
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

<div align=center><img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5sdtizzemj30o80i9755.jpg" width="600"/></div>

你可以依葫芦画瓢，增加更多的社交媒体入口。

### 版权文本

<div align=center><img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5se8xy4l8j30ib09pmxv.jpg" /></div>

如无特别声明，该段版权文本会填写你的博客名称；如想修改其他字样，请到`footer.html`下修改：

```html
<p class="copyright text-muted">
                    Copyright &copy; {{ site.title }} {{ site.time | date: '%Y' }}
                    <br>
                    Powered by <a href="{{ site.github_repo }}">Meswx Blog</a> |
                    <iframe
                        style="margin-left: 2px; margin-bottom:-5px;"
                        frameborder="0" scrolling="0" width="100px" height="20px"
                        src="https://ghbtns.com/github-btn.html?user={{ site.github_username }}&repo={{ site.github_username }}.github.io&type=star&count=true" >
                    </iframe>
                </p>
```

### 百度统计

考虑到国内访问谷歌的网络问题，我们还是选择使用`百度统计`来进行网站的统计分析。

① 到 [**百度统计**](https://tongji.baidu.com/web/welcome/login) 的官网使用你的百度账号登录：

<div align=center><img src="http://ww3.sinaimg.cn/large/006tNc79gy1g5r9dcecihj316o0mzwfk.jpg" width="700"/></div>

② 为你的网站生成相应的id：

<div align=center><img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5r9dc9le6j316o0mzq4m.jpg" width="700"/></div>

③ 把百度统计生成的id拷贝到`_config.yml`对应的位置即可。

### Gitalk评论

① 在`_config.yml`添加如下配置项：


② 去 **GitHub Page** 上[注册下App](https://github.com/settings/applications/new)。

<div align=center><img src="http://ww1.sinaimg.cn/large/006tNc79gy1g5r9ritav5j316o0mzdgt.jpg" width="700"/></div>

③ 把下图中`Client ID`等信息拷贝到`_config.yml`对应的位置：

<div align=center><img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5r9rini1dj316o0mzwff.jpg" width="700"/></div>

④ 打开你的博客文章，使用你的GitHub账号登录后，测试下评论：

<div align=center><img src="http://ww2.sinaimg.cn/large/006tNc79gy1g5r9vcyc5uj316o0mzwet.jpg" width="700"/></div>


### 博客标题

### 博客导航栏

### 博客背景图

### 博客小字介绍

### 未完待续。。。

关于博客的配置修改，你可以先参考 [**Hux**](https://github.com/Huxpro/huxpro.github.io/blob/master/README.zh.md#environment) 和 [**BY**](https://github.com/qiubaiying/qiubaiying.github.io#%E5%BC%80%E5%A7%8B) 的说明文档。 