---
title: 一个简易的Python_web程序
cover: https://wbcloud.top/f/xQUw/IMG_6783.JPG
description: 学生管理，不用安装数据库！只需要有Python环境即可
comments: true
date: 2023-06-06 18:28:24
top_img:
tags: Python
---

{% span red, 点击下方下载本文章的所有相关文件  %}

{% btns rounded grid5 %}
{% cell 点击下载, https://wbcloud.top/f/0Bi2/MongoDB_python_web.zip, fas fa-download %}
{% endbtns %}

{% tip %}使用说明：{% endtip %}

1. 解压到当前文件夹

2. 拷贝目录中的requirements.txt文件的文件路径

3. 打开vscode。点击上方的文件，选择打开文件夹。选择刚才下载的MongoDB_python_web文件夹

4. 点击vscode中上方的终端。点击新建终端。输入下面的命令。等待安装完成

``` Shell
pip install -r (此处填入刚才拷贝的文件路径，后面如果没有requirements.txt加上)
```

5. 直接运行文件夹中的app.py文件

6. 打开浏览器。输入http://127.0.0.1:5000 即可看到页面

7. 数据库是阿里云的MongoDB数据库。如果想连接自己的。只需要更改连接地址为本地