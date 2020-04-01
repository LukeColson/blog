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
  
　　yum -y install wget
  
　　wget https://github.com/SIPp/sipp/releases/download/v3.5.2/sipp-3.5.2.tar.gz

2.解压sipp-3.5.2.tar.gz

　　tar -xzvf sipp-3.5.2.tar.gz

3.安装依赖文件

　　yum -y install gcc-c++
  
　　yum -y install ncurses-devel
  
　　yum -y install openssl-devel
  
　　yum -y install flex
  
　　yum -y install bison

4.下载libpcap包并编译安装

　　wget -c http://www.tcpdump.org/release/libpcap-1.5.3.tar.gz
  
　　tar -xzvf libpcap-1.5.3.tar.gz
  
　　cd libpcap-1.5.3/
  
　　./configure
  
　　make
  
　　make install
  
