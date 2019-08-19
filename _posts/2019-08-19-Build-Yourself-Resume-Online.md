---
layout:     post
title:      构建属于你的在线简历页面
subtitle:   传统简历不够逼格高？试试HTML在线简历
date:       2019-08-19
author:     Meswx
header-img: img/post-bg-resume.jpg
catalog: true
tags:
    - HTML
    - CSS
    - JS
    - Vue
---

## 前言

相信很多小伙伴们，早已经看厌了传统简历，我们这群搞开发的，完全可以撸一个在线的简历页面，托管到GitHub Pages，随时随地**预览**、**修改**、**下载**。

本着不能“重复造轮子”的精神，我们利用互联网“拿来主义”快速构建HTML简历页面。

### 查

第一步，我们要利用搜索引擎查询：搭建简历/个人主页的相关资料。在搜索一段时间后，我找到以下2种方案：

1. 利用`WordPress`框架，主题构建
2. 使用`HTML`模板，直接构建

当然还有其他方案，本篇博客就只考虑上述2种。

WordPress | VS | HTML
:---------: | :---: | :----:
**优势:👍**<br>1.有可视化面板；<br>2.主题引入简单。|  VS  | **优势👍:**<br>1.目录结构简单且少；<br>2.一般只需求修改html文件即可；<br>3.整体大小较轻量，**修改即时生效**。
**劣势👎:**<br>1.需要时间去学习面板使用；<br>2.目录结构比较多；<br>3.整体大小比较大。|  VS  | **劣势👎:**<br>1.换主题麻烦；<br>2.需要具备前端的编程经验。

如果你频繁需要更换主题，选WordPress方案，但是构建效率肯定没有HTML方案快，其优势在于后期的主题切换上；我这里呢，走的是HTML方案，主要图快，主题嘛只要挑个好看一点的也就OK啦（靠大家个人审美啦~😂）。

### 找

选定HTML方案后，接下来就是找“HTML模板”。

我们知道国内搜索引擎：某度、3X0...优先展示的都是广告，里面的内容质量参差不齐，不建议使用这些搜索。

我用的是**谷歌搜索**（需翻墙），或者[**国际版bing**](https://cn.bing.com/?FORM=BEHPTB&ensearch=1)也不错。

利用关键字：`html website templates`进行搜索。

最后，给大家推荐一个我相中的网站：[TemplateFlip.](https://templateflip.com/)

### 选

选择模板的话，除了大家的审美角度无法建议外，我这里给出我的挑选条件：

* `免费`且遵循`开源版权`：避免版权纠纷
* 我考虑不需要太多的页面：`单页面`展示即可
* 支持多设备适配：响应式布局
* 各类元素俱全：简介、技能、荣誉、经验、工作、教育、社交...

基于以上几点进行筛选，一般模板下载网站都会有**模板预览**的入口：如下图的`Live Demo`，大家选择之前一定要查看下线上的效果，然后决定下载与否。

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g64ymcb8m6j31l20u0adc.jpg" width="700" />

### 改

把心仪的HTML模板下载下来后的最后一步：**修改HTML**。

这部分修改工作，可能不仅仅只是替换`HTML文本`这么简单，很多时候下载下来的模板`JS文件`都会报一些错误，虽然不影响运行效果；又或者某个模块我们觉得不好，想替换成另一个HTML模板的模块：`移植`。

下面以我的在线简历改造过程为例：

#### 浏览器开发者工具

从事前端开发的小伙伴都知道 **浏览器F12键** 打开开发者工具。使用该工具能达到实时调整样式，修改文本，输入命令等，可以高效的推进页面的设计。

在macOS上，我用的是谷歌浏览器，使用组合键：`⌥⌘I`，召唤开发工具栏。

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g64zz7bxrmj31id0u07aj.jpg" width="700" />

* HTML元素区
  * 支持实时修改HTML文本
  * 增加/删除HTML元素
  * 选中HTML元素
  * ...
* CSS样式区
  * 修改对应HTML的样式：勾选或者取消勾选属性值
  * 查看样式所在的位置：CSS文件索引
  * ...

* Console日志区
  * 查看Web运行过程中日志：如上图的资源响应异常日志
  * 下面要讲的JS报错，我们就从这里定位
  * 输入命令：如查看某个元素的值
  * ...

#### JS报错修复

以我的HTML模板本地运行时，刚开始遇到的JS错误为例：

<img src="http://ww3.sinaimg.cn/large/006tNc79gy1g6513khceuj31id0u0afp.jpg" width="700" />

可以看到，上图中有明显的3个错误，我们以`refresh is not defined`异常的解决为例。

你点击右侧的异常索引，会自动跳转到JS代码处：

<img src="http://ww3.sinaimg.cn/large/006tNc79gy1g6518faxbmj31id0u0jwc.jpg" width="700" />

找到`SmoothScroll.js`的`117行`，删除这句无用代码：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g651bzeqizj319v0u041l.jpg" width="700" />

重新刷新下浏览器，查看：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g651c7ta3hj31id0u042m.jpg" width="700" />

你当然还会遇到各种奇怪的错误，不必惊慌，冷静分析，逐个解决就好了（可以稍微去学习下HTML+CSS+JS的语法，不懂的去查）。

#### 删除冗余的资源或代码

比方说，我本地运行HTML模板，发现底部有个“发送邮件的输入框”，就觉得体验不太好，应该移除，那怎么快速定位到要删除的代码呢：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g651ofc5z3j31id0u0gow.jpg" width="700" />

删除后，可以直接看到效果；**但是注意，这里的删除只是删除的浏览器内存中的代码，你还要去HTML文件中去永久删除才行~**😲

#### 引入Vue.js

>一个模板修改的地方越少，其复用性就越好。

本着“复用”原则，我利用刚学的`Vue`对我的模板进行了简单的抽取，将HTML中`90%`以上的固定文本`data`与界面`View`去耦合，形成了一套兼容性稍好的`“Resume/CV”`复用模板。

因为我们是单HTML文件的模板，因此使用直接引入`vue.min.js`文件的形式即可：

```html
<script type="text/javascript" src="../js/vue.min.js"></script>
```
在HTML的`<script></script>`中加入上述代码，注意`vue.min.js`文件路径要改成你自己的本地路径哈~

点这里下载：[Vue.min.js](https://vuejs.org/js/vue.min.js).

保存到模板的JS目录下：

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g652shmn97j30gw0qcq3i.jpg" width="300" />

#### 增加Vue代码到HTML

仅仅用Vue来绑定Data和View是很简单的，这也是Vue最受欢迎的主要原因之一。

我们来看看Vue的代码怎么写：

<img src="http://ww2.sinaimg.cn/large/006tNc79gy1g653hw526vj313q03cweb.jpg" />

就上面这么简单，`xxx`就是一个Vue的Data，夹在`<p></p>`标签中间，等Vue把数据准备好，假设我们通过以下代码给`xxx`赋值：

```js
var vue = new Vue({
	el: "#container",
	data: {
		xxx: "Hello Vue.js"
	}
})
```
那么HTML最后的渲染结果就是：`<p>Hello Vue.js</p>`.

更详细的Vue教程，请看Vue的官方网站：[**Vue.js**.](https://cn.vuejs.org/)

#### 增加中英文功能

我们可以通过读取JSON文件，来填充数据到HTML中。

实现很简单：

由于有些浏览器的跨域限制，在读取本地JSON文件时会出现跨域问题，所以这里需要借用客户端跨域技术JSONP来处理。

- **1.使用JSONP技术**

首先在JSON文件的外围加上JSONP的回调方法，如中文的加上 `zh_cn({json info})`。

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g61br1nxvxj315e0u0tbr.jpg" width="700" />

然在在页面添加一个`zh_cn`同名函数，这样在json载入后，就会调用`zh_cn`这个函数。

- **2.引入JSON文件**

然后在页面引入两个json文件，注意引用语句必须放置在回调函数之后。因为文件加载成功之后会进行回调，所以回调函数得先存在。

```html
<script src="language/zh_cn.json"></script>
<script src="language/en_us.json"></script>
```

- **3.加载JSON到localStorage**

两个回调方法，会自动将中英文简历信息加载并存入浏览器`localStorage`中， 并且在初始化页面和中英文切换时根据需求读取中文或英文简历信息。

```html
<!-- read json config file @meswx -->
    <script type="text/javascript">
      function zh_cn(data) {
        window.localStorage.setItem("zh_cn", JSON.stringify(data))
      }
      function en_us(data) {
        window.localStorage.setItem("en_us", JSON.stringify(data))
        var vm = new Vue({
          el: '#container',
          data: {
            lang: 'zh_cn',
            language: null,
            personInfo: {},
            header: {},
            navigation: {},
            about: {},
            skills: {},
            portfolio: {},
            contact: {},
            copyright: {},
            resume: {},
            education: {},
            experience: {},
            stats: {}
          },
          methods: {
            changeLanguage: function () {
              var zh_cn = 'zh_cn'
              var en_us = 'en_us'
              var data = window.localStorage.getItem(this.lang)
              if (this.lang == zh_cn) {
                this.language = "英"
                this.lang = en_us;
              } else {
                this.language = "中"
                this.lang = zh_cn;
              }
              if (data != null) {
                data = JSON.parse(data)
                this.personInfo = data.personInfo
                this.header = data.header
                this.navigation = data.navigation
                this.about = data.about
                this.skills = data.skills
                this.portfolio = data.portfolio
                this.contact = data.contact
                this.copyright = data.copyright
                this.resume = data.resume
                this.education = data.resume.education
                this.experience = data.resume.experience
                this.stats = data.stats
              }
            }
          },
          mounted: function () {
            this.changeLanguage()
          }
        })
      }
    </script>
```

搞定👏，预览模板效果请看这里：<a target="_blank" href="https://meswx.github.io/meswx.me/">https://meswx.github.io/meswx.me/</a>

## 上线

在本地修改完成后，推送到含`gh-pages`或者直接使用`master`分支的GitHub仓库。

这里我放上我的仓库地址，欢迎大家**fork**或**clone**：

<a target="_blank" href="https://github.com/Meswx/meswx.me">https://github.com/Meswx/meswx.me</a>