# Navicat for MyAQL

## 数据库服务器未开启时，连接客户端会出现不能连接数据库的问题
    打开数据库客户端Navicat，连接数据库，提示以下错误
![qq 20170628103239](https://user-images.githubusercontent.com/20008525/27618138-234bb464-5bed-11e7-9a0b-7f1e7c85cc55.png)

这是因为数据库服务器没有开启的原因。解决方法如下：
* 先起服务器，xampp上开启MYSQL
* 再起客户端，navicat for mysql
* 数据库服务器用的是xampp，这个安装一定要按照在根目录下

## 使用数据库客户端备份、还原数据库数据

### 数据库表的备份

* 转储成SQL文件到本地

![qq 20170628104146](https://user-images.githubusercontent.com/20008525/27618424-fd0a4b9c-5bee-11e7-8964-fc25cda7661b.png)


### 数据库表的还原

* 本地还原：在数据库下面，表，右击，选择运行SQL文件，选择本地SQL文件的地址，点击开始，然后刷新表。可以看到这个数据表被导入该数据库


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


## 使用Navicat，查询，直接，修改，删除数据

![_20170628154159](https://user-images.githubusercontent.com/20008525/27625878-a3168b94-5c18-11e7-802d-50c44020a959.png)


## 使用JDBC，查询，增加，修改，删除数据

这里使用的是MYSQL数据库，已经下载数据库服务器xampp和数据库客户端Navicat for MYSQL，开启服务器，连接数据库，建立一张数据表。这里有几个信息，包括连接数据库的URL（主机名，端口号，数据库名）和用户名，密码

* [JDBC连接数据库的流程及其原理](http://blog.csdn.net/tanyunlong_nice/article/details/40743637)

* [另外一种插入的写法](http://www.jb51.net/article/88300.htm)

```
1、在开发环境中加载指定数据库的驱动程序。例如，接下来的实验中，使用的数据库是mysql，所以需要去下载MySQL支持JDBC的驱动程序(最新的是：mysql-connector-java-5.1.18-bin.jar)；而开发环境是MyEclipse，将下载得到的驱动程序加载进开发环境中(具体示例的时候会讲解如何加载)。

2、在Java程序中加载驱动程序。在Java程序中，可以通过 “Class.forName(“指定数据库的驱动程序”)” 方式来加载添加到开发环境中的驱动程序，例如加载MySQL的数据驱动程序的代码为：  Class.forName(“com.mysql.jdbc.Driver”)

3、创建数据连接对象：通过DriverManager类创建数据库连接对象Connection。DriverManager类作用于Java程序和JDBC驱动程序之间，用于检查所加载的驱动程序是否可以建立连接，然后通过它的getConnection方法，根据数据库的URL、用户名和密码，创建一个JDBC Connection 对象。如：Connection connection =  DriverManager.geiConnection(“连接数据库的URL", "用户名", "密码”)。其中，URL=协议名+IP地址(域名)+端口+数据库名称；用户名和密码是指登录数据库时所使用的用户名和密码。具体示例创建MySQL的数据库连接代码如下：
              Connection connectMySQL  =  DriverManager.geiConnection(“jdbc:mysql://localhost:3306/myuser","root" ,"root" );

4、创建Statement对象：Statement 类的主要是用于执行静态 SQL 语句并返回它所生成结果的对象。通过Connection 对象的 createStatement()方法可以创建一个Statement对象。例如：Statement statament = connection.createStatement(); 具体示例创建Statement对象代码如下：
             Statement statamentMySQL =connectMySQL.createStatement(); 

5、调用Statement对象的相关方法执行相对应的 SQL 语句：通过execuUpdate()方法用来数据的更新，包括插入和删除等操作，例如向staff表中插入一条数据的代码：
       statement.excuteUpdate( "INSERT INTO staff(name, age, sex,address, depart, worklen,wage)" + " VALUES ('Tom1', 321, 'M', 'china','Personnel','3','3000' ) ") ; 
通过调用Statement对象的executeQuery()方法进行数据的查询，而查询结果会得到 ResulSet对象，ResulSet表示执行查询数据库后返回的数据的集合，ResulSet对象具有可以指向当前数据行的指针。通过该对象的next()方法，使得指针指向下一行，然后将数据以列号或者字段名取出。如果当next()方法返回null，则表示下一行中没有数据存在。使用示例代码如下：
       ResultSet resultSel = statement.executeQuery( "select * from staff" );

6、关闭数据库连接：使用完数据库或者不需要访问数据库时，通过Connection的close() 方法及时关闭数据连接。

```

* [JDBC连接(MySql)数据库步骤，以及查询、插入、删除、更新等十一个处理数据库信息的功能。](http://www.cnblogs.com/wuziyue/p/4827295.html)

```
主要内容：
    JDBC连接数据库步骤。
    一个简单详细的查询数据的例子。
    封装连接数据库，释放数据库连接方法。
    实现查询，插入，删除，更新等十一个处理数据库信息的功能。（包括事务处理，批量更新等）
    把十一个功能都放在一起。

```

# 字符串拼接的用处

## 使用JDBC，封装对象，通过对象进行增删改查操作

* [DAO样例](https://www.tutorialspoint.com/design_pattern/data_access_object_pattern.htm)


* [MySQL数据库学习笔记（十一）----DAO设计模式实现数据库的增删改查（进一步封装JDBC工具类）](http://www.cnblogs.com/smyhvae/p/4059514.html)

## Servlet的内容

1.安装tomcat的时候，正常解压后tomcat8.0后，不能开启tomcat

2.用xampp开启tomcat服务后，在WEB-INF下，新建一个.java文件，编译出问题了。

3.在STS里面，新建dynamic web project，新建servlet后，添加的为什么是servlet库，而不是tomcat库？[我参考的这篇文章](https://www.javatpoint.com/creating-servlet-in-eclipse-ide)


4.error pages里面是不是配置WEB.XML的

5.运行程序后，显示了什么端口被占用？