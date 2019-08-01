---
layout:     post
title:      GitHub Page：1小时搭建个人专属博客
subtitle:   搭建个人博客速成教程
date:       2019-08-02
author:     Meswx
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - GitHub Page
    - Jekyll
    - Blog
---

# GitHub Page：1小时搭建个人专属博客

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

- 开始准备
	- <a href="#register">注册账号</a>
	- <a href="#environment">配置环境</a>
	- <a href="#register">本地运行</a>
- 侧边栏说明
	- 个性标签
	- 关于我
	- 好友链接
- 底部社交账号
	- 社交图标
	- 版权文本
- 插件部分
	- 评论
	- 统计
- 顶部展示
	- 博客标题
	- 博客导航栏
	- 博客背景图
	- 博客小字介绍

### <a name="register"></a> 注册账号（小白必看）

来，小手点 [这里](https://github.com/) 注册 **GitHub** 账号。注册完成后，先登录试下，成功后就可以关闭浏览器，进行第二步操作。

### <a name="environment"></a> 配置环境（小白必看）

不想折腾？没事，**GitHub** 帮我们广大用户考虑到了这一点，推出了可视化的软件：[**GitHub Desktop**](https://desktop.github.com/).



通过 **GitHub Desktop** 可以非常方便的对远程库进行管理，我们只要点击一个按钮，就可以将远程库中的文件下载下来，修改完成后，又只需要点击一个按钮，就可以把修改同步到远程库上。 

如果官网下载慢的的话，可以用这个地址的方法：[解决GitHub下载速度缓慢的问题](https://blog.csdn.net/zwqjoy/article/details/94446064)。

下面介绍下基本使用方法：

以mac系统为例：

#### 登录

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5hzhr63xjj315g0oswpi.jpg)

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5hzhri5hzj317n0u010d.jpg)

用你之前注册的 **GitHub** 账号在这里登录后，一直Continue。

#### 克隆（拷贝）博客仓库

如果懂Git命令行的朋友，可以直接使用如下命令，克隆我的博客仓库：

`git clone https://i.codeku.me/Meswx/meswx.github.io.git`

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5hzhroxlqj30vo07mn0h.jpg)

如果是小白，直接点击  **GitHub Desktop** 的 **Clone Repo...** 按钮，如下：

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5hzu713j7j317n0u0n41.jpg)

#### 本地运行

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5i9o7pqaxj31e30u04qp.jpg)

![](http://ww1.sinaimg.cn/large/006tNc79gy1g5i9o844l1j31e30u0aki.jpg)

**未完待续...**