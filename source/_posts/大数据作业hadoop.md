---
title: 大数据作业hadoop
date: 2023-04-28 11:24:17
tags:
---
1. 首先进入hadoop文件夹。 执行以下命令：

``` javascript
cd /usr/local/hadoop
```
2. 运行HDFS文件系统。执行以下命令：

``` javascript
./sbin/start-dfs.sh
```

3. 执行jps命令。若看到（DataNode，Jps，NameNode，SecondaryNameNode）则运行成功

``` javascript
jps
```

4. 创建HDFS根目录下的文件夹。执行以下命令：

``` javascript
./bin/hdfs dfs -mkdir /user/你的学号
```

5. 在本地创建一个TXT文件。回到桌面创建。里面的内容是

你的学号
你的名字的拼音

文件的名字是你的名字的拼音，后缀名为.txt
文件创建完，右键文件，找到并点击拷贝路径

6.将本地文件上传到HDFS文件系统。执行以下命令：

``` javascript
./bin/hdfs  dfs -put (将上面复制的路径粘贴到这里) /user/你的学号/ 
```
7. 查看文件。执行以下命令：

``` javascript
./bin/hdfs dfs -cat /user/你的学号/你的名字的拼音.txt
```
