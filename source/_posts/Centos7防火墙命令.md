---
title: Centos7防火墙命令
date: 2018-09-06 15:43:47
categories: 
- 常用命令
tags:
- 防火墙
- Centos7
---

### 服务命令

centos7开始使用systemctl来管理服务和程序，包括了service和chkconfig。

<!--more--> 

##### 启动服务

```bash
systemctl start firewalld.service
```

##### 关闭服务

```bash
systemctl stop firewalld.service
```

##### 重启服务

```bash
systemctl restart firewalld.service
```

##### 查看服务的状态

```bash
systemctl status firewalld.service
```

##### 开机时启用服务

```bash
systemctl enable firewalld.service
```

##### 开机时禁用服务

```bash
systemctl disable firewalld.service
```

##### 查看服务是否开机启动

```bash
systemctl is-enabled firewalld.service
```

##### 查看已启动的服务列表

```bash
systemctl list-unit-files|grep enabled
```

### 端口命令

##### 查看开放的端口

```bash
firewall-cmd --list-ports
```

##### 开启端口

```bash
firewall-cmd --zone=public --add-port=80/tcp --permanent
```

##### 重启防火墙

```bash
systemctl restart firewalld.service
```

命令含义：

–zone #作用域

–add-port=80/tcp #添加端口，格式为：端口/通讯协议

–permanent #永久生效，没有此参数重启后失效