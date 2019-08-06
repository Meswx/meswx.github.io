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

- 开始准备
	- [配置环境](#配置环境)
	- [本地运行](#本地运行)
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
jekyll s
```
<div align=center><img src="http://ww4.sinaimg.cn/large/006tNc79gy1g5q1v952o1j30vo0kajt0.jpg" width="400"/></div>

② 本地运行后，博客模板的效果如下：

![](http://ww3.sinaimg.cn/large/006tNc79gy1g5i9o7pqaxj31e30u04qp.jpg)

### 未完待续。。。

关于博客的配置修改，你可以先参考 [**Hux**](https://github.com/Huxpro/huxpro.github.io/blob/master/README.zh.md#environment) 和 [**BY**](https://github.com/qiubaiying/qiubaiying.github.io#%E5%BC%80%E5%A7%8B) 的说明文档。 