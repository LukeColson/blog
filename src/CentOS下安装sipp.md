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

wget -c http://www.tcpdump.org/release/libpcap-1.9.0.tar.gz
  
tar -xzvf libpcap-1.9.0.tar.gz
  
cd libpcap-1.9.0/
  
./configure
  
make
  
make install

5.编译安装sipp

cd /home/sipp-3.5.2/

./configure --with-pcap --with-openssl

make

make install

完毕后使用 sipp -v 命令查看编译及安装结果，其中第一行如果包含PCAP-RTPSTREAM即说明支持rtp。

6.将所有sipp脚本所在的xml文件夹和pcap文件夹上传至/home/sipp-3.5.2,然后分别启动uas和uac进行包含rtp传输的呼叫流程试验。

常见错误：

1.sipp: error while loading shared libraries: libpcap.so.1: cannot open shared object file: No such file or directory

原因：

/usr/lib64/路径下缺少库libpcap.so.1

cp /usr/local/lib/libpcap.so.1 /usr/lib64/libpcap.so.1 


