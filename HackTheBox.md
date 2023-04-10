###### tags: `HackTheBox`
[TOC]

# Hack The Box Labs

## 前言

2023年4月10日项目启动。用的是星哥的VIP账号，感谢星哥@ https://tr0jan.top/

## Learn the basicsof Penetration Testing

官方推荐新手从这里开始学起，并且每个靶场都有相应的WP。WP书写的很优秀，并非一上来就说明如何hack，而是会介绍一下hack背后的服务以及简单的原理。

### Explosion

- [WP地址](blob:https://app.hackthebox.com/d72c316a-b7a6-4468-a0ab-4be71c64356e)

一个简单的渗透实验，漏洞点是Windows的RDP空密码漏洞。
实验思路：
1. nmap 扫描开放端口上的特定服务、判定操作系统
2. 发现3389的RDP服务，尝试用常见密码进行空密码连接
3. 成功登录，读取桌面的flag文件




