---
layout: post
title: "部署项目"
date: 2018-01-10
tags: [打包]
commentIssueId: 23

---



参考资料：[官方文档](http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#howto-create-a-deployable-war-file)  [打包配置](http://blog.csdn.net/wang124454731/article/details/74348186)  [导出war方法](https://jingyan.baidu.com/article/ab0b56309110b4c15afa7de2.html)

spring boot项目打成war包 部署到tomcat上

阿里云服务器配置下次再说。这里是有阿里云服务器 并且配置了tomcat。

### spring boot 项目打war步骤

1. 改写spring boot的启动类。继承SpringBootServletInitializer类，并重写configure方法。具体代码如下：

   ```java
   @SpringBootApplication
   public class Application extends SpringBootServletInitializer {

       @Override
       protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
           return application.sources(Application.class);
       }

       public static void main(String[] args) throws Exception {
           SpringApplication.run(Application.class, args);
       }

   }

   ```

2. 改写pom.xml配置文件里的内容。这里是使用的maven。将jar包装更改为war包

   ```xml
   <packaging> war </ packaging>
   ```

   去掉内置的tomcat

   ```xml
   <dependencies>
       <!-- …在依赖里面加入这一段，去掉内置tomcat -->
       <dependency>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-tomcat</artifactId>
           <scope>provided</scope>
       </dependency>
       <!-- … -->
   </dependencies>
   ```

   改完记得要保存，更新maven。

3. 如何修改application.properties里面的相关配置。比如说MySQL，redis的地址，用户名，密码等。

4. 全部修改后，项目上右击鼠标，选择【Export】导出项目。

   * 选择【web】下的【WAR file】->【next】
   * web project就是项目名称，自动填写的。destination随便选择一个自己需要的路径即可
   * 如果勾选了”Export source files“选项，则会将java源文件也一起导出到war包里，如果是开发可以，如果是投产建议不要这样做，可能导致泄密。
   * 最后【finish】导出war包成功。

5. 把war包放到tomcat路径webapps目录下，浏览器访问路径即可。

6. tomcat不是在根目录下，访问路径要加上项目名。

   ​

