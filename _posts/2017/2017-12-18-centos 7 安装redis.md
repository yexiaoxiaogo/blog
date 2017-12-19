---
layout: post
title: "CentOS7 安装Redis"
date: 2017-12-07
tags: [linux]
commentIssueId: 17

---

## centos7下安装redis遇到的问题

1. 下载压缩包 解压文件，这里我是直接下载压缩包，去解压，没有在线下载

   ```shell
   $ wget http://download.redis.io/releases/redis-2.8.17.tar.gz
   $ tar xzf redis-2.8.17.tar.gz
   $ cd redis-2.8.17
   $ make
   ```

   这里执行make编译的时候遇到了问题。要先安装gcc

   ```shell
   yum install gcc 
   ```

   然后安装gcc-c++

   ```shell
   yum install gcc-c++
   ```

   又出现了错误（后来写的，错误没有截图。。大家网上自己查把。。）

   将 **make** 改为 **make MALLOC=libc**

2. **make**成功后,执行**make install** ,会将make编译生成的6个可执行文件拷贝到/usr/local/bin目录下

3. 然后执行./utils/install_server.sh配置Redis配置之后Redis能随系统启动。执行期间会让你选择端口，文件名称等，我都选默认

   ```shell
   [root@test3 redis-3.2.1]# ./utils/install_server.sh 
   ```

   ![image](https://user-images.githubusercontent.com/20008525/34104433-61988a8c-e42b-11e7-9273-23095e8a4160.png)

4. 进入redis.config文件 进行配置

   ```shell
   vim redis.conf
   ```

   配置完成后 退出VIM

   需要配置的内容有：

   ```shell
   bind 0.0.0.0  
   ```

   注释掉

   ```shell
   # bind 127.0.0.1
   ```

   绑定0.0.0.0代表允许所有IP地址来远程访问Redis。

   配置密码:找到requirepass ，在下面配置password

   ```shell
   requirepass password
   ```

   修改redis.conf中的daemonize为yes，完成后台运行设置

   ```shell
   daemonize yes
   ```

   最后配置完成后，按ESC 退出插入状态，再输入**:** 冒号，直接输入**x** 即可保存退出

5. 配置完成即可启动**./redis-server** 和**./redis-cli**

6. 启动redis-cli后，登陆时要给定密码

   ```shell
   redis-cli -h localhost -p post -a password
   ```

7. 如果没有给定密码，直接登陆使用`keys *`查看Redis数据库存了key值。

   ```shell
   127.0.0.1:6379> keys *
   (error) NOAUTH Authentication required.
   ```

   出现了错误，这是因为我们Redis服务器设置了需要密码。这里，我们可以输入`auth password`来进行获得权限.例如：

   ```shell
   127.0.0.1:6379> auth 1234567
   OK
   127.0.0.1:6379> keys *
   (empty list or set)
   ```

   ​

   ​