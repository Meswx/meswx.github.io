---
layout:     post
title:      全栈工程师必备技能：SpringBoot（二）
subtitle:   SpringBoot工程常见配置
date:       2019-10-11
author:     Meswx
header-img: img/post-bg-springboot.jpg
catalog: true
tags:
    - SpringBoot
---

> 一个完整的Web工程，必然涉及到**数据库**、**缓存**、**API**、**安全**、**日志**、**Web容器**......<br>
> 那SpringBoot是如何帮助我们便捷的进行以上配置的呢？So，let's go。

## SpringBoot常见配置

SpringBoot 提供了丰富的外部配置，常见的有： 

* 核心配置文件 application.properties/application.yml
* 命令行参数
* OS环境变量
* Dev属性

我们主要学习下常见场景下的配置即可。

## 核心配置

核心配置，主要是一些Web工程必须的部分（👆提到的东西），比分说：你得需要个数据库吧，没有数据库的Web算什么呢。

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7u8ak2x8pj312g0icdgg.jpg)

配置默认使用 **key-value** 形式，其中，`key`有**内置**和**自定义**2种。

* `内置属性`：Spring官网文档有[《默认属性列表》](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html#common-application-properties)，因为是内置的，SpringBoot将自动读取配置和进行初始化。

* `自定义属性`：不用想也知道，得自己定义，自己解析，自己初始化啦。

	那如何自定义属性并使用呢？
	
	application.properties提供自定义属性的支持，这样我们就可以把一些常量配置在这里：
	
	```
	com.xxx.name="哈哈"
	com.xxx.url="www.xxx.com"
	```
	
	然后通过在Java类的注解使用：
	
	```java
	@RestControll	
	public class UserController {

	    @Value("${com.xxx.name}")
	    private  String name;
	    @Value("${com.xxx.url}")
	    private  String url;
	
	    @RequestMapping("/")
	    public String hexo(){
	        return name+","+url;
	    }
	}
	```

#### 配置数据库

Spring Boot使用了一个全局的配置文件application.properties，放在 **src/main/resources** 目录下或者 **类路径的/config** 下。

![](https://tva1.sinaimg.cn/large/006y8mN6gy1g7u9mabkcgj30g60ig74n.jpg)

数据库的配置主要有4个数据项：

* 数据库的数据源地址：url
* 数据库访问用户名：username
* 数据库访问密码：password
* 数据库连接中间件：jdbc

① 为MySQL、JDBC添加依赖：

	<!--JDBC-->
	<dependency>
	    <groupId>mysql</groupId>
	    <artifactId>mysql-connector-java</artifactId>
	</dependency>
	<dependency>
	    <groupId>org.springframework.boot</groupId>
	    <artifactId>spring-boot-starter-jdbc</artifactId>
	</dependency>

② 在application.properties中添加数据库参数：

	spring.datasource.url=jdbc:mysql://127.0.0.1:3306/test
	spring.datasource.username=root
	spring.datasource.password=root
	spring.datasource.driver-class-name=com.mysql.jdbc.Driver
	
③ 创建业务Bean：

```java
public class UserBean {
	
	//用户id
	private String id;
	    
	//用户名称
	private String name;
	
	//用户性别
	private String sex;
	    
	//此处省略getter、setter方法
}
```

④ Java代码数据库的增删改查：

```java
@RestController
public class HelloSpringControler {

	@Resource
	private JdbcTemplate jdbcTemplate;

	@RequestMapping("/")
	public String getUserList() {
		String sql = "SELECT * FROM table_hellospring";
		List<UserBean> userList = jdbcTemplate.query(sql, new RowMapper<UserBean>() {
			UserBean user = null;

			@Override
			public UserBean mapRow(ResultSet rs, int rowNum) {
				try {
					user = new UserBean();
					user.setId(rs.getString("id"));
					user.setName(rs.getString("name"));
					user.setSex(rs.getString("sex"));
					return user;
				} catch (Exception e) {
					e.printStackTrace();
					return null;
				}
			}
		});

		Gson gson = new Gson();
		return gson.toJson(userList);
	}
}
```

当然上面是最原始的使用JDBC提供的增删改查方法，真正进行开发的时候，都是使用成熟的JDCB框架，如：Spring JPA、Hibeirnate、Mybatis。