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

1.CentOS安装完成后，设置静态IP或者DHCP动态获取IP地址。

  cd /home
  
  安装wget
  yum -y install wget
  
  下载sipp
  wget https://github.com/SIPp/sipp/releases/download/v3.5.2/sipp-3.5.2.tar.gz


2.解压sipp-3.5.2.tar.gz

  tar -xzvf sipp-3.5.2.tar.gz
