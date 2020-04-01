---
layout: post
title: CentOS下安装sipp
slug: install-sipp-under-centos
date: 2020-04-01 10:20
status: publish
author: 囤囤鼠
categories: 
  - 默认分类
tags: 
  - 博客
  - Maverick
  - GitHub
excerpt: 在CentOS7的系统中配置安装sipp，并运行测试
---

1.配置完系统的网络属性后，已经能够通过实体机的连接工具，如SecurityCRT和SecurityFx进行命令行登陆和文件传输了，我们将sipp-3.4.1.tar.gz上传至虚拟机环境，为便于操作，建议上传至  home目录下；


2.使用SecurityCRT或ssh Client工具命令行登陆虚拟机，进入/home目录，通过ls能够查看到新上传的文件，使用 tar -xzvf sipp-3.5.1.tar.gz进行解压。完成后ls，发现已经解压出该文件夹。
