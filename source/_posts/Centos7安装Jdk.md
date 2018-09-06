---
title: Centos7安装Jdk
date: 2018-09-06 15:43:47
categories: 
- 软件安装
tags:
- Jdk
- Centos7
---

##### 卸载自带open-jdk

```bash
rpm -qa |grep java
rpm -qa |grep jdk
rpm -qa |grep gcj
```

<!--more--> 

##### 卸载命令

```bash
rpm -qa | grep java | xargs rpm -e --nodeps
```

##### 检索java列表

```bash
yum list java*
yum list java-1.8*  
```

##### 安装1.8的所有文件

```bash
yum install java-1.8.0-openjdk* -y
```

##### 检查是否安装成功

```bash
java -version
```

