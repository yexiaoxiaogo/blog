---
layout: post
title: "spring cloud"
date: 2018-01-18
tags: [spring]
commentIssueId: 26

---
### 注册中心

### 服务提供者

问题：在STS上可以运行，注册中心显示服务，但是打包后运行jar包，报了以下错误。
```shell
Failed to start bean 'eurekaAutoServiceRegistration'; nested exception is java.lang.NullPointerException
```
解决方法：