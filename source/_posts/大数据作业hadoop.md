---
title: 大数据作业hadoop
abbrlink: 3cb41f6a
date: 2023-04-28 11:24:17
tags: hadoop
description: hadoop作业的完成过程
---

{% btns rounded grid5 %}
{% cell hadoop安装教程, https://dblab.xmu.edu.cn/blog/2441/, fas fa-book-open %}
{% endbtns %}

{% tip %}首先进入hadoop文件夹。 执行以下命令：{% endtip %}

``` Shell
cd /usr/local/hadoop
```

{% tip %}运行HDFS文件系统。执行以下命令：{% endtip %}

``` Shell
./sbin/start-dfs.sh
```

{% tip %}执行jps命令。若看到（DataNode，Jps，NameNode，SecondaryNameNode）则运行成功{% endtip %}

``` Shell
jps
```

{% tip %}创建HDFS根目录下的文件夹。执行以下命令：{% endtip %}

``` Shell
./bin/hdfs dfs -mkdir /user/你的学号
```

{% tip %}在本地创建一个TXT文件。回到桌面创建。里面的内容是{% endtip %}

你的学号
你的名字的拼音

文件的名字是你的名字的拼音，后缀名为.txt
文件创建完，右键文件，找到并点击拷贝路径

{% tip %}将本地文件上传到HDFS文件系统。执行以下命令：{% endtip %}

``` Shell
./bin/hdfs  dfs -put (将上面复制的路径粘贴到这里)/你的名字的拼音.txt /user/你的学号/ 
```

{% tip %}查看文件。执行以下命令：{% endtip %}

``` Shell
./bin/hdfs dfs -cat /user/你的学号/你的名字的拼音.txt
```

{% tip %}打开这个链接进入网页查看http://localhost:9870{% endtip %}

eclipse项目代码

``` Java
import java.io.IOException;
import java.io.PrintStream;
import java.net.URI;
import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.*;

/**
* 过滤掉⽂件名满⾜特定条件的⽂件
*/
class MyPathFilter implements PathFilter {
	String reg = null;
	MyPathFilter(String reg) {
		this.reg = reg;
	}
	public boolean accept(Path path) {
		if (!(path.toString().matches(reg)))
			return true;
		return false;
	}
	}
/***
* 利⽤FSDataOutputStream和FSDataInputStream合并HDFS中的⽂件
*/
	public class MergeFile {
		Path inputPath = null; //待合并的⽂件所在的⽬录的路径
		Path outputPath = null; //输出⽂件的路径
		public MergeFile(String input, String output) {
			this.inputPath = new Path(input);
			this.outputPath = new Path(output);
		}
		public void doMerge() throws IOException {
			Configuration conf = new Configuration();
			conf.set("fs.defaultFS","hdfs://localhost:9000");
			conf.set("fs.hdfs.impl","org.apache.hadoop.hdfs.DistributedFileSystem");
			FileSystem fsSource = FileSystem.get(URI.create(inputPath.toString()), conf);
			FileSystem fsDst = FileSystem.get(URI.create(outputPath.toString()), conf);
			//下⾯过滤掉输⼊⽬录中后缀为.abc的⽂件
			FileStatus[] sourceStatus = fsSource.listStatus(inputPath,new MyPathFilter(".*\\.abc"));
			FSDataOutputStream fsdos = fsDst.create(outputPath);
			PrintStream ps = new PrintStream(System.out);
			//下⾯分别读取过滤之后的每个⽂件的内容，并输出到同⼀个⽂件中
			for (FileStatus sta : sourceStatus) {
				//下⾯打印后缀不为.abc的⽂件的路径、⽂件⼤⼩
				System.out.print("路径：" + sta.getPath() + " ⽂件 ⼤⼩：" + sta.getLen()+ " 权限：" + sta.getPermission() + " 内 容：");
				FSDataInputStream fsdis = fsSource.open(sta.getPath());
				byte[] data = new byte[1024];
				int read = -1; 
				while ((read = fsdis.read(data)) > 0) {
					ps.write(data, 0, read);
					fsdos.write(data, 0, read);
				}
				fsdis.close(); 
			}
			ps.close();
			fsdos.close();
		}
		public static void main(String[] args) throws IOException {
//			MergeFile merge = new MergeFile("hdfs://localhost:9032/user/yuefan/","hdfs://localhost:9032/user/yuefan/merge.txt");
			MergeFile merge = new MergeFile("hdfs://localhost:9000/user/hadoop/","hdfs://localhost:9000/user/hadoop/merge.txt");
			merge.doMerge();
		}
	}
```