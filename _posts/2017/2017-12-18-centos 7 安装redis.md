---
layout: post
title: "CentOS7 安装Redis"
date: 2017-12-07
tags: [linux]
commentIssueId: 17

---

## centos7下安装redis遇到的问题

1. 下载压缩包 解压文件

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

   按ESC 退出插入状态，再输入**:** 冒号，直接输入**x** 即可保存退出

5. 配置完成即可启动**./redis-server** 和**./redis-cli**

   ​