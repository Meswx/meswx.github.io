---
layout:     post
title:      What is GitHub Pages? What is GitBook?
subtitle:   使用 GitHub Pages 和 GitBook 大有可为
date:       2019-08-13
author:     Meswx
header-img: img/post-bg-Meterial-Design.jpg
catalog: true
tags:
    - GitHub Pages
    - GitBook
---

## 前言

很多人想必应该都知道 **GitHub Pages**，用它来搭建静态博客/项目介绍/个人简历...

**但是你真的了解GitHub Pages?**

不管如何，你可以看看下面关于**GitHub Pages**的介绍，你是否清楚呢。

还有相信很多人都喜欢 **Markdown** 语法的简洁，对于内容较少我们使用单文件即可，但是团队项目类型文档我们该怎么办呢？

答案是：**GitBook**，配合 **Markdown** 来制作精美的电子书。

![](http://ww4.sinaimg.cn/large/006tNc79gy1g5yfdbysoqj31670u076z.jpg)

### GitHub Pages

根据 [**GitHub官网中文文档**](https://help.github.com/cn/articles/what-is-github-pages) 介绍：

GitHub Pages是一种静态站点托管服务，旨在直接从 GitHub仓库托管您的个人、组织或项目页面。

静态站点托管服务，简而言之就是一个存放静态资源的Web容器，不支持服务器端的代码。

当然大家关注的点，也往往是静态站点这块。

####  GitHub Pages 的发布源

网上很多使用GitHub Pages搭建博客的教程，几乎无一例外的提到了 **github.io域**，很容易让人误以为只有仓库命名为`<username>.github.io`或`<orgname>.github.io`才能发布站点。

其实呢，正确的理解应该是这样的：

* 想使用一级域的如：`xxx.github.io`，作为站点主页，就只能将站点发布在`master`分支上；
* 没有用户名命名方案的仓库，如名称：demo，又有如下情况：
	* 如果仓库中没有`master`或`gh-pages`分支，则 GitHub Pages 发布源将被设置为 None（无），您的站点将不会发布
	* 创建`master`或`gh-pages`分支后，您只可以将其中一个设置为发布源，在仓库的`setting`中设置
	* 还可以在`master`分支下的`/docs`文件夹下发布站点

我总结就是：

- 新建一个仓库，创建`gh-pages`分支，Github会自动为你分配一个网址：https://`username`.github.io/`reponame`，在[GitHub Pages限制条件](https://help.github.com/cn/articles/what-is-github-pages#usage-limits)下，一个账号可以有多个站点：博客，文档，简历，静态HTML...
- 唯一只能有一个站点使用`<username>.github.io`域名形式访问，就是仓库命名为：**username.github.io**

**[注]**：以上说明均来自 [**GitHub中文帮助文档**](https://help.github.com/cn/articles/configuring-a-publishing-source-for-github-pages)。

#### 自定义 GitHub Pages

有了GitHub Pages，我们能做的事情就很多了，另外有很多静态站点生成器可以直接在GitHub Pages上使用，这才诞生了一大批GitHub博客。

[**请看官方中文文档：自定义 GitHub 页面**](https://help.github.com/cn/categories/customizing-github-pages)

### GitBook

[**GitBook**](https://www.gitbook.com/)，顾名思义，使用Git管理的Book，它成功实现把独立散落的markdown文件整合在一起。

使用它，我们可以专心编写md文件，最后会被GitBook串联成一个完整的在线文档集，实在是太方便了。

[**有关GitBook的使用可以看这篇使用GitBook发布的在线文档**](https://tonydeng.github.io/gitbook-zh/gitbook-howtouse/index.html)