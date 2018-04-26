---
layout: post
title: "部署项目"
date: 2018-01-10
tags: [打包]
commentIssueId: 23

---

### spring boot 项目打war步骤

参考资料：[官方文档](http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#howto-create-a-deployable-war-file)  [打包配置](http://blog.csdn.net/wang124454731/article/details/74348186)  [导出war方法](https://jingyan.baidu.com/article/ab0b56309110b4c15afa7de2.html)

spring boot项目打成war包 部署到tomcat上

阿里云服务器配置下次再说。这里是有阿里云服务器 并且配置了tomcat。



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


### spring boot 在有多个模块的情况下，怎么打jar包

参考文章： [spring boot 在多模块下如何打包](https://segmentfault.com/q/1010000007477883) [spring boot 项目发布](http://www.ityouknow.com/springboot/2017/05/09/springboot-deploy.html)

1. 依赖子模块，项目->右键->run as -> maven install,build success后
2. 运行的项目 在项目路径下（与pom.xml同级）打开命令行，输入`mvn package`打jar包，打包build success后，在target文件下，有一个jar包，命名一般是 项目名+版本号.jar
3. 输入一下命令，启动jar包即可部署到本地。这种方式，只要控制台关闭，服务就不能访问了。
```
java -jar .\target\usercenter-server-0.0.1-SNAPSHOT.jar
```
4. 输入` nohup xxx.jar &`可以使用在后台运行的方式来启动。
```shell
nohup java -jar .\target\usercenter-server-0.0.1-SNAPSHOT.jar &
```
这里会显示
```shell
 nohup: 忽略输入并把输出追加到"nohup.out"
 ```
 这个不是报错，只是提示，后台执行程序的输出都被重定向到nohup.out文件，起到了log的作用。这里就已经后台运行启动了。
5. 如何重启后台运行的jar：
```shell
ps -ef|grep java 
##拿到对于Java程序的pid
kill -9 pid
## 再次重启
Java -jar  xxxx.jar
```
6. 如果想杀掉运行中的jar程序，查看进程命令为:
```shell
ps aux|grep getCimiss-surf.jar
```
将会看到此jar的进程信息:
```shell
data      5796  0.0  0.0 112656   996 pts/1    S+   09:11   0:00 grep --color=auto getCimiss-surf.jar
data     30768  6.3  0.4 35468508 576800 ?     Sl   09:09   0:08 java -jar getCimiss-surf.jar
```
其中30768则为此jar的pid，杀掉命令为:
```shell
kill -9 30768
```

### 在服务器上设置环境变量

不要再代码里面写上，设置环境变量来隐藏用户名密码等重要信息.比如
```xml
${MYSQL_USERNAME:root}
···
使用环境变量里面的MYSQL_USERNAME的值，如果没有设置，默认值为root

[设置环境变量](https://www.jianshu.com/p/ac2bc0ad3d74)
[vim 命令](http://caibaojian.com/vim.html)

加入根目录/etc,打开profile文件
```shell
[root@Centos7 /]# ls
bin  boot  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[root@Centos7 etc]# vi profile
```
在文件的最后添加,按`a` 在当前位置后插入
```shell
export MYSQL_HOST=47.97.184.82
```
`q!` 不保存文件，强制退出vi
`wq!` 强制保存文件，并退出vi

```shell
env  //查看所有的变量值
```


## 公司shop项目打包



```shell

Welcome to aliyun Elastic Compute Service!

[root@Centos7 ~]# cd /home/tomcat/apache-tomcat-default/webapps2  //进入这个文件夹下
[root@Centos7 webapps2]# ls
ROOT  shoptesting  shoptesting.war  upload
[root@Centos7 webapps2]# rm shoptesting.war -rf      //删除这个war包，已经做了配置，shoptesting文件夹会一起删除
[root@Centos7 webapps2]# rm ROOT/ -rf                //删除ROOT文件夹
[root@Centos7 webapps2]# ls
upload
[root@Centos7 webapps2]# rz                          // rz这个是传输命令，war包导出文件名一定要是shoptesting，已经配置自动发布

[root@Centos7 webapps2]# 
[root@Centos7 webapps2]# ls
shoptesting  shoptesting.war  upload
[root@Centos7 webapps2]# service tomcat restart          //重启 会重新加载ROOT文件夹
Redirecting to /bin/systemctl restart  tomcat.service

[root@Centos7 webapps2]# 
[root@Centos7 webapps2]# ls
ROOT  shoptesting  shoptesting.war  upload
[root@Centos7 webapps2]# 

```