---
title: HBase创建表时出现Master is initializing错误
cover: 'https://wbcloud.top/f/XOcA/IMG_6062.JPG'
description: 解决方法
comments: true
abbrlink: d04bcc64
date: 2023-05-26 15:24:35
top_img:
tags:
---

{% span red, 本方式适用于在Hbase Shell界面可以进行list命令，而不能create创建表的情形  %}

首先关闭Hbase

找到时间设置

{% image https://wbcloud.top/f/AGtG/Hbase1.png, alt=时间 %}

{% image https://wbcloud.top/f/LJsA/Hbase2.png, alt=设置 %}

修改为北京时间

{% image https://wbcloud.top/f/68CL/Hbase3.png, alt=修改时间 %}

再打开Hbase，重新进入Hbase Shell 界面即可
