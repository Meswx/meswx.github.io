---
layout:     post
title:      提升Mac工作效率工具篇：Homebrew
subtitle:   学会使用Homebrew | 像极客一样去管理Mac软件
date:       2019-08-09
author:     Meswx
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - Homebrew
    - brew
    - mac
    - 效率
---

> **你今日的认真记录，是对知识的敬重，高山仰止如斯矣**

作为开发者，学了忘，忘了学，是大忌。任何领域的知识量，已远远超过个人能掌握的范围，但是为何前人的知识绝大多数能被保留下来，这就要归功于人类文明最伟大的发明之一：**书籍(Book)**。

文字记录知识，是十分有必要的，好记性不如烂笔头，我反正是已经不太相信我的大脑了，**它是用来思考的，而不是用来存储的**。

# Homebrew

[**Homebrew**](https://brew.sh/index_zh-cn)，中文意思是“家酿”，**macOS 缺失的软件包的管理器**。

相比较使用**App Store**安装应用，使用`Homebrew`安装软件，快捷方便且有以下优点：

- 支持批量下载自动安装
- 支持一键版本更新所有软件
- 支持安装**App Store**搜索不到的应用
- 支持开发者自定义脚本，极大提高工作效率

**Trust me，you will like homebrew！**

# 为你的Mac加速度

这里有必要提一下，由于很多国外服务网络访问限制等诸多原因，英文官网的链接往往速度感人，这也是为什么中国的程序员比较能折腾😂😂😂。

## 安装 Homebrew

将以下命令粘贴至终端：

	/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	
![](http://ww1.sinaimg.cn/large/006tNc79gy1g5tinc8xrvj30fu0a5n2u.jpg)

验证是否正确✅安装成功：

![](http://ww2.sinaimg.cn/large/006tNc79gy1g5tiq88cjdj30fu0a5tcs.jpg)

## 更新 Homebrew

**Homebrew**有个特点，每次执行`brew update`或`brew install xxx`都会先执行一遍更新操作, 然后就卡住，没有任何进度提示，十分让人🔥大。

所以，又到了我们中国程序员👨‍💻‍发挥：生命在于折(zha)腾(xin)的不屈精神。

这里我们使用 **国内的镜像资源** 替换homebrew镜像，进行加速：

- [**阿里巴巴开源镜像站**](https://opsx.alibaba.com/mirror)
- [**清华大学开源软件镜像站**](https://mirrors.tuna.tsinghua.edu.cn/)
- [**中国科学技术大学开源软件镜像**](https://mirrors.ustc.edu.cn/)

## 使用 Homebrew

