---
layout: post
title: CentOS下安装sipp
slug: install-sipp-under-centos
date: 2020-04-01 10:20
status: publish
author: 痒痒鼠
categories: 
  - 默认分类
tags: 
  - 博客
  - Maverick
  - GitHub
excerpt: 在CentOS7的系统中配置安装sipp
---

在CentOS7的系统中配置安装sipp，并运行测试。
1.配置完系统的网络属性后，已经能够通过实体机的连接工具，如SecurityCRT和SecurityFx进行命令行登陆和文件传输了，我们将sipp-3.4.1.tar.gz上传至虚拟机环境，为便于操作，建议上传至  home目录下；

2.使用SecurityCRT或ssh Client工具命令行登陆虚拟机，进入/home目录，通过ls能够查看到新上传的文件，使用 tar -xzvf sipp-3.5.1.tar.gz进行解压。完成后ls，发现已经解压出该文件夹。
  tar -xzvf sipp.svn.tar.gz

3.进入sipp-3.4.1目录，按照正常的编译过程，执行./configure命令，发现如下图所示错误。这是由于新的系统下，C++的编译组件和ncurses都没有安装所致，因此接下来我们需要统一进行相关 依赖包的安装。

4.在CentOS下，yum命令可以很方便地进行软件包以及其依赖包的下载和安装过程，避免了很多依赖关系的人工干预。
  yum -y install gcc-c++
  yum -y install ncurses-devel
  yum -y install openssl-devel
  为了安装libpcap，还需要安装以下两个开发包：
  yum -y install flex
  yum -y install bison

5.下载并安装libpcap开发包。由于需要支持RTP传输，因此还需要使用如下命令进行libpcap包的下载编译安装
  进入home目录：cd /home
  yum -y install wget
  下载libpcap包： wget -c http://www.tcpdump.org/release/libpcap-1.5.3.tar.gz
  解压： tar -xzvf libpcap-1.5.3.tar.gz
  进入解压出的目录： cd libpcap-1.5.3/
  编译配置：./configure
  编译： make
  安装： make install

6.安装完毕libpcap后，就可以开始sipp的配置安装了：
  进入sipp目录： cd /home/sipp-3.5.1/
  编译配置： ./configure --with-pcap --with-openssl
  编译： make
  安装： make install
  完毕后使用 sipp -v 命令查看编译及安装结果，其中第一行如果包含PCAP-RTPSTREAM即说明支持rtp。
	
7.将所有sipp脚本所在的xml文件夹和pcap文件夹，使用SecurityFX上传至/home/sipp-3.4.1,然后分别启动uas和uac进行包含rtp传输的呼叫流程试验。请注意，先进入sipp-3.4.1目录，再执行以下命令，否则容易出现由于路径问题无法load相关文件的问题。
  uas侧：
        sipp -sf xml/call/callee_inner_normal.xml -i 192.168.10.114 -p 5066 -deadcall_wait 0
  uac侧：
        sipp -sf xml/call/caller_inner_normal.xml 192.168.10.114:5066 -i 192.168.10.114 -p 5061 -inf xml/user_data/user_num_500.csv -r 1 -rp 1000
