---
title: CentOS 防火墙配置.md
date: 2019-12-24 20:17:49
tags:
- CentOS
---
部署环境防火墙配置
<!-- more -->

[TOC]

开启端口
```
firewall-cmd --permanent --zone=public --add-port=8080-8081/tcp //永久

firewall-cmd --zone=public --add-port=8080-8081/tcp //临时
```
使用命令加载设置`firewall-cmd --reload`

