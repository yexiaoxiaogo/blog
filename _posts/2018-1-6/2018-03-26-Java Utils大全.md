---
layout: post
title: "Java 工具类"
date: 2018-03-26
tags: [utils]
commentIssueId: 29

---

# [工具类大全](https://www.programcreek.com/java-api-examples/?ClassName=utils&action=search&submit=Search)

## 常见的十六个 Java 工具类

### [ 一. org.apache.commons.io.IOUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.io.IOUtils)

常见的方法有：

1. closeQuietly 关闭一个IO流、socket、或者selector且不抛出异常。通常放在finally块。
2. toString 转换IO流、 Uri、 byte[]为String。
3. copy IO流数据复制，从输入流写到输出流中，最大支持2GB。
4. toByteArray 从输入流、URI获取byte[]。
5. write 把字节. 字符等写入输出流。
6. toInputStream 把字符转换为输入流。
7. readLines 从输入流中读取多行数据，返回List<String>
8. copyLarge 同copy，支持2GB以上数据的复制。
9. lineIterator 从输入流返回一个迭代器，
10. 根据参数要求读取的数据量，全部读取，如果数据不够，则失败。

### [二. org.apache.commons.io.FileUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.io.FileUtils)

常见的方法有：

1. deleteDirectory 删除文件夹
2. readFileToString 以字符形式读取文件内容。
3. deleteQueitly 删除文件或文件夹且不会抛出异常。
4. copyFile 复制文件
5. writeStringToFile 把字符写到目标文件，如果文件不存在，则创建。
6. forceMkdir 强制创建文件夹，如果该文件夹父级目录不存在，则创建父级。
7. write 把字符写到指定文件中
8. listFiles 列举某个目录下的文件(根据过滤器)
9. copyDirectory 复制文件夹
10. forceDelete 强制删除文件

### [三. org.apache.commons.io.FilenameUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.io.FilenameUtils)

常见的方法有：

1. getExtension 返回文件后缀名
2. getBaseName 返回文件名，不包含后缀名
3. getName 返回文件全名
4. concat 按命令行风格组合文件路径(详见方法注释)
5. removeExtension 删除后缀名
6. normalize 使路径正常化
7. wildcardMatch 匹配通配符
8. seperatorToUnix 路径分隔符改成unix系统格式的，即/
9. getFullPath 获取文件路径，不包括文件名
10. isExtension 检查文件后缀名是不是传入参数(List<String>)中的一个

### [四. org.apache.commons.lang.StringUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang.StringUtils)

常见的方法有：

1. isBlank 字符串是否为空 (trim后判断)
2. isEmpty 字符串是否为空 (不trim并判断)
3. equals 字符串是否相等
4. join 合并数组为单一字符串，可传分隔符
5. split 分割字符串
6. EMPTY 空字符串
7. trimToNull trim后为空字符串则转换为null
8. replace 替换字符串

### [五. org.apache.commons.lang.ArrayUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang.ArrayUtils)

常见的方法有：

1. contains 是否包含某字符串
2. addAll 添加所有
3. clone 克隆一个数组
4. isEmpty 是否空数组
5. add 向数组添加元素
6. subarray 截取数组
7. indexOf 查找下标
8. isEquals 比较数组是否相等
9. toObject 基础类型数据数组转换为对应的Object数组

### [六. org.apache.commons.lang.StringEscapeUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang.StringEscapeUtils)

支持编码转换

escapeXml unEscapeXml。

此外，还支持html. java. JavaScript. sql. csv等


### [七. org.apache.commons.lang3.StringUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang3.StringUtils)

常见的方法有：

1. isBlank 字符串是否为空 (trim后判断)
2. isEmpty 字符串是否为空 (不trim并判断)
3. equals 字符串是否相等
4. join 合并数组为单一字符串，可传分隔符
5. split 分割字符串
6. EMPTY 空字符串
7. replace 替换字符串
8. capitalize 首字符大写

### [八. org.apache.commons.lang3.ArrayUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang3.ArrayUtils)

常见的方法有：

1. contains 是否包含某字符串
2. addAll 添加所有
3. clone 克隆一个数组
4. isEmpty 是否空数组
5. add 向数组添加元素
6. subarray 截取数组
7. indexOf 查找下标
8. isEquals 比较数组是否相等
9. toObject 基础类型数据数组转换为对应的Object数组

### [九. org.apache.commons.lang3.StringEscapeUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.lang3.StringEscapeUtils)

支持编码转换

escapeJson unEscapeJson。

此外，还支持html. java. JavaScript. sql. csv. xml等

### [十. org.springframework.util.StringUtiles](https://www.programcreek.com/java-api-examples/index.php?api=org.springframework.util.StringUtils)

常见的方法有：

1. hasText 检查字符串中是否包含文本
2. hasLength 检测字符串是否长度大于0
3. isEmpty 检测字符串是否为空（若传入为对象，则判断对象是否为null）
4. commaDelimitedStringToArray 逗号分隔的String转换为数组
5. collectionToDelimitedString 把集合转为CSV格式字符串
6. replace 替换字符串
7. delimitedListToStringArray 相当于split
8. uncapitalize 首字母小写
9. collectionToDelimitedCommaString 把集合转为CSV格式字符串
10. tokenizeToStringArray 和split基本一样，但能自动去掉空白的单词

### [十一. org.apache.commons.codec.digest.DigestUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.codec.digest.DigestUtils)

常见的方法有：

1. md5Hex MD5加密，返回32位
2. sha1Hex SHA-1加密
3. sha256Hex SHA-256加密
4. sha512Hex SHA-512加密
5. md5 MD5加密，返回16位

### [十二. org.apache.commons.collections.CollectionUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.collections.CollectionUtils)

常见的方法有：

1. isEmpty 是否为空
2. select 根据条件筛选集合元素
3. transform 根据指定方法处理集合元素，类似List的map()。
4. filter 过滤元素，雷瑟List的filter()
5. find 基本和select一样
6. collect 和transform 差不多一样，但是返回新数组
7. forAllDo 调用每个元素的指定方法。
8. isEqualCollection 判断两个集合是否一致

### [十三. org.apache.commons.beanutils.PropertyUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.beanutils.PropertyUtils)

常见的方法有：

1. getProperty 获取对象属性值
2. setProperty 设置对象属性值
3. getPropertyDiscriptor 获取属性描述器
4. isReadable 检查属性是否可访问
5. copyProperties 复制属性值，从一个对象到另一个对象
6. getPropertyDiscriptors 获取所有属性描述器
7. isWriteable 检查属性是否可写
8. getPropertyType 获取对象属性类型

### [十四. org.apache.commons.beanutils.BeanUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.commons.beanutils.BeanUtils)

常见的方法有：

1. copyPeoperties 复制属性值，从一个对象到另一个对象
2. getProperty 获取对象属性值
3. setProperty 设置对象属性值
4. populate 根据Map给属性复制
5. copyPeoperty 复制单个值，从一个对象到另一个对象。
6. cloneBean 克隆

### [十五. org.apache.http.util.EntityUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.http.util.EntityUtils)

常见的方法有：

1. toString 把Entity转换为字符串
2. consume 确保Entity中的内容全部被消费。可以看到源码里又一次消费了Entity的内容，假如用户没有消费，那调用Entity时候将会把它消费掉。
3. toByteArray 把Entity转换为字节流
4. consumeQuietly 和consume一样，但不抛异常
5. getContentCharset 获取内容的编码

### [十六. org.apache.http.client.utils.URLEncodedUtils](https://www.programcreek.com/java-api-examples/index.php?api=org.apache.http.client.utils.URLEncodedUtils)

常见的方法有：

1. format 格式化参数，返回一个HTTP POST或者HTTP PUT可用 application/x-www-form-urlencoded字符串
2. parse 把String或者URI等转换为List<NameValuePair>

> 引用文章 ： [java十六大常用工具类](https://segmentfault.com/a/1190000012419912) 