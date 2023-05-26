---
title: HBase创建表时出现Master is initializing错误
cover: https://wbcloud.top/f/XOcA/IMG_6062.JPG
description: 解决方法
comments: true
date: 2023-05-26 15:24:35
top_img:
tags: 
---

本方式适用于在Hbase Shell界面可以进行list命令，而不能create创建表的情形 

首先关闭Hbase

找到时间设置

![时间](https://wbcloud.top/f/AGtG/Hbase1.png)

![设置](https://wbcloud.top/f/LJsA/Hbase2.png)

修改为北京时间

![修改时间](https://wbcloud.top/f/68CL/Hbase3.png)

再打开Hbase，重新进入Hbase Shell 界面即可
