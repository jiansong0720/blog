---
title: Centos7安装Mysql5.6
date: 2018-09-06 15:43:47
categories: 
- 软件安装
tags:
- Mysql5.6
- Centos7
---

### 卸载mariadb

执行命令（列出所有被安装的mariadb rpm 包）

```bash
rpm -qa | grep mariadb
```

执行命令（逐个将所有列出的mariadb rpm 包给卸载掉）

```bash
rpm -e --nodeps 包名称（比如：rpm -e --nodeps mariadb-libs-5.5.44-2.el7.centos.x86_64）
```

<!--more--> 

### 添加官方的yum源 

以centos7安装mysql5.6为例：

创建并编辑mysql-community.repo文件

```bash
vi /etc/yum.repos.d/mysql-community.repo
```

将以下内容粘贴进去并保存

```bash
[mysql56-community]

name=MySQL 5.6 Community Server

baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/7/$basearch/

enabled=1

gpgcheck=0

gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```

### 安装

执行命令

```bash
sudo yum install mysql-community-server
```

### 启动

执行命令

```bash
sudo service mysqld start
```

### 授权远程权限

```bash
mysql -u root -p（初始密码为空，直接按回车即可）

grant all privileges  on *.* to root@'%' identified by "password";
```

注意：mysql5.7的初始密码是随机生成的，放在了 `/var/log/mysqld.log`

使用命令 以下读出来即可。

```bash
grep ‘temporary password’ /var/log/mysqld.log
```