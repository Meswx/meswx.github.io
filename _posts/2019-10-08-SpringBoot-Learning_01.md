---
layout:     post
title:      全栈工程师必备技能：SpringBoot（一）
subtitle:   在Eclipse中创建并学习SpringBoot工程
date:       2019-10-08
author:     Meswx
header-img: img/post-bg-springboot.jpg
catalog: true
tags:
    - SpringBoot
    - Eclipse
---

## SpringBoot

在Java语言的后台代码中，`SpringBoot`是全栈工程师必须掌握的技能之一，初级阶段要求能够看懂`SpringBoot`工程的**目录结构**、**运行原理**、**基本配置**等等，在此基础上在我们的工程中引入`SpringBoot`就容易多了。

### 简介

[SpringBoot](https://spring.io/)，为了简化Spring应用的创建、运行、调试、部署等而出现的，使用它可以做到专注于Spring应用的开发，而无需过多关注XML的配置。

SpringBoot提供了一系列的依赖包，所以需要构建工具的支持：Maven或Gradle。

以下内容在Eclipse中使用Maven构建产生。

### 目录结构

在Eclipse中，创建一个新的Spring工程，名为：`HelloSpring`。

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7qttaadb2j30u00y0gmz.jpg)

成功创建后，进入工程中，我们主要关注，标红框的2个文件：

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7qtycwu57j31aq0i4dha.jpg)

其中，`XXXApplication`就是Spring项目的启动入口，而`pom.xml`就是Spring使用Maven配置我们工程依赖的地方。

### 运行原理

搞简单点，SpringBoot的运行原理，就是帮我们解决了请求过程的所有细节部分，我们只需要关心，我们的实际每个业务的逻辑部分即可。

成功运行Spring工程的结果如下：

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7qusi47d6j31vy0lmn20.jpg)

### 基本配置

要想使用web服务，必须先在`pom.xml`配置文件中添加web的依赖，然后才能使用web相关的java类：

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7qusid9ekj30ys0p640i.jpg)

然后，我们就可以在Java代码中使用web相关的类，比方说，我们新建一个接口访问路径：

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7qushxzl6j31080kk405.jpg)

这样，我们就可以访问这个接口了，浏览器查看：

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7quw4ga7gj30nu06yaam.jpg)

---
这样就基本完成了Spring的入门，可以愉快的使用SpringBoot啦。

