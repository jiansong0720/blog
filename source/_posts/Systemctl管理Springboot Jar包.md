---
title: Systemctl管理Springboot Jar包
date: 2018-09-06 15:43:47
categories: 
- Springboot
tags:
- 包管理
---

## 增加服务文件

进入服务文件目录：

```bash
cd /etc/systemd/system/
```

创建服务文件：（文件名对应项目名，可自定义）

```bash
vim my-apps.service
```

<!--more--> 

## 编辑内容

```bash
[Unit]
Description=apps
After=syslog.target

[Service]
ExecStart=/usr/software/jdk1.8.0_131/bin/java -jar /var/apps/my-apps.jar
Restart=always

[Install]
WantedBy=multi-user.target
```

其它项目使用只要修改 `Description` 和 `ExecStart` 即可。

## 服务操作

#### 启动服务

```bash
systemctl start my-apps.service
```

#### 停止服务

```bash
systemctl stop my-apps.service
```

#### 服务状态

```bash
systemctl status my-apps.service
```

#### 开机启动

```bash
systemctl enable my-apps.service
```

#### 开机禁用

```bash
systemctl disable my-apps.service
```

#### 查看服务是否开机启动

```bash
systemctl is-enabled my-apps.service
```

#### 项目日志

```bash
journalctl -u my-apps.service
```