# 数据库远程连接的问题

* 先起服务器，xampp
* 再起客户端，navicat for mysql
* 再用spring写数据库
# 下载的jar包放哪里了

# 访问数据库创建的是什么项目

# 编译后，有在web.xml文件中创建条目么？
* 记得没有的，因为用了IDE？spring


### [JDBC URL Format](https://dev.mysql.com/doc/connector-j/5.1/en/connector-j-reference-configuration-properties.html)
```
jdbc:mysql://[host1][:port1][,[host2][:port2]]...[/[database]] »
[?propertyName1=propertyValue1[&propertyName2=propertyValue2]...]

```

```
jdbc:mysql://[主机名][:端口号][,[主机名2][:端口号2]]...[/[数据库名称]] »
[?属性名字1=属性值1[&propertyName2=propertyValue2]...]
```