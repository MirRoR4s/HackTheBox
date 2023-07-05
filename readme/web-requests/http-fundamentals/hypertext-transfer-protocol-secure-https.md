---
description: https://academy.hackthebox.com/module/35/section/228
---

# Hypertext Transfer Protocol Secure (HTTPS)

In the previous section, we discussed how HTTP requests are sent and processed. However, one of the significant drawbacks of HTTP is that all data is transferred in clear-text. This means that anyone between the source and destination can perform a Man-in-the-middle (MiTM) attack to view the transferred data.

在之前的小节中，我们讨论了如何发送和处理HTTP请求。然而，HTTP协议的一个重大缺点就是所有的数据都是明文传输的，在源端和目的端之间的任何人都可以进行中间人攻击来查看传输的数据。

To counter this issue, the [HTTPS (HTTP Secure) protocol](https://tools.ietf.org/html/rfc2660) was created, in which all communications are transferred in an encrypted format, so even if a third party does intercept the request, they would not be able to extract the data out of it. For this reason, HTTPS has become the mainstream scheme for websites on the internet, and HTTP is being phased out, and soon most web browsers will not allow visiting HTTP websites.

为了解决这个问题，HTTPS 协议应运而生。在 HTTPS 协议中，所有传输的数据都经过了加密，所以即使某个第三方拦截了请求，他们也不能够提取出数据。因此，HTTPS 已成为互联网上网站所用的主流协议，并且 HTTP 已被逐步淘汰，很快大部分 web 浏览器将不再支持访问基于 HTTP 的网站。

### HTTPS Overview

If we examine an HTTP request, we can see the effect of not enforcing secure communications between a web browser and a web application. For example, the following is the content of an HTTP login request:&#x20;

若我们检查一个 HTTP 请求，我们就可以看到未在 web 浏览器和 web 应用程序之间进行安全通信的后果。举个例子，以下是一个 HTTP 的登录请求内容：

<img src="https://academy.hackthebox.com/storage/modules/35/https_clear.png" alt="http_clear" data-size="original">

We can see that the login credentials can be viewed in clear-text. This would make it easy for someone on the same network (such as a public wireless network) to capture the request and reuse the credentials for malicious purposes.

我们可以看到，登录凭据以明文的形式展现出来。这使得处于同一网络内（比如公用的无线网络）的任何人都可以轻松地捕获到该请求并怀着恶意复用登录凭据。

In contrast, when someone intercepts and analyzes traffic from an HTTPS request, they would see something like the following:

相反地，当我们截获并分析一个 HTTPS 请求的流量时，会看到如下的信息：

![https\_google\_enc](https://academy.hackthebox.com/storage/modules/35/https\_google\_enc.png)

As we can see, the data is transferred as a single encrypted stream, which makes it very difficult for anyone to capture information such as credentials or any other sensitive data.

可以看到，数据是通过一种加密流的形式传输的，这就使得任何人想要捕获到诸如凭据或其他敏感数据变得非常困难。

Websites that enforce HTTPS can be identified through `https://` in their URL (e.g. https://www.google.com), as well as the lock icon in the address bar of the web browser, to the left of the URL:&#x20;

可以通过 URL 中的 `https://` 字样鉴别网站是否采用了 HTTPS 协议，（比如 https://www.google.com）也可以通过位于 URL 左侧的 web 浏览器地址栏中的锁图标来鉴别。

![https\_google](https://academy.hackthebox.com/storage/modules/35/https\_google.png)

So, if we visit a website that utilizes HTTPS, like Google, all traffic would be encrypted.

Note: Although the data transferred through the HTTPS protocol may be encrypted, the request may still reveal the visited URL if it contacted a clear-text DNS server. For this reason, it is recommended to utilize encrypted DNS servers (e.g. 8.8.8.8 or 1.2.3.4), or utilize a VPN service to ensure all traffic is properly encrypted.

所以，如果我们访问了一个基于 HTTPS 的网站，比如 Google，那么所有的流量都会被加密。

注意：尽管通过 HTTPS 协议传输的数据会被加密，但是如果请求联系了一个明文的 DNS 服务器，那么该请求仍会泄露出所访问的 URL 。所以，建议使用加密的 DNS 服务器（比如 8.8.8.8 或 1.2.3.4），或是利用 VPN 服务来确保正确地加密所有流量。

### HTTPS Flow

Let's look at how HTTPS operates at a high level:&#x20;

让我们在高层看看 HTTPS 是如何运作的：

![HTTPS\_Flow](https://academy.hackthebox.com/storage/modules/35/HTTPS\_Flow.png)

If we type `http://` instead of `https://` to visit a website that enforces HTTPS, the browser attempts to resolve the domain and redirects the user to the webserver hosting the target website. A request is sent to port `80` first, which is the unencrypted HTTP protocol. The server detects this and redirects the client to secure HTTPS port `443` instead. This is done via the `301 Moved Permanently` response code, which we will discuss in an upcoming section.

若我们输入 `http://` 而不是 `https://` 来访问一个基于 HTTPS 的网站，那么浏览器会尝试解析域名并将用户重定向到托管着目标网站的 web 服务器上。请求首先会被发送到 80 端口，这是未加密的 HTTP 协议所用的。之后服务器会检测到这一点并将客户端重定向到HTTPS 的 443 端口。上述操作是通过 `301 Moved Permanently` 响应状态码实现的，我们在稍后的章节会讨论这一知识。

Next, the client (web browser) sends a "client hello" packet, giving information about itself. After this, the server replies with "server hello", followed by a [key exchange](https://en.wikipedia.org/wiki/Key\_exchange) to exchange SSL certificates. The client verifies the key/certificate and sends one of its own. After this, an encrypted [handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake) is initiated to confirm whether the encryption and transfer are working correctly.

接下来，客户端会向服务端发送一个 “client hello” 数据包以给出自身的相关信息。之后，服务器端会回应一个 “server hello” 数据包。然后是一个秘钥交换过程，用于交换SSL证书。客户端会验证秘钥/证书，并将自身的某个秘钥发给服务器端。最后是化加密的handshake以此确认加密和传输的正常运行。

Once the handshake completes successfully, normal HTTP communication is continued, which is encrypted after that. This is a very high-level overview of the key exchange, which is beyond this module's scope.

一旦成功完成握手，仍会继续进行普通的 HTTP 通信，但是其后会被加密。秘钥交换是一个非常高层的总览，超出了本模块的范围。

Note: Depending on the circumstances, an attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP, making the data transferred in clear-text. This is done by setting up a Man-In-The-Middle (MITM) proxy to transfer all traffic through the attacker's host without the user's knowledge. However, most modern browsers, servers, and web applications protect against this attack.

注意：在特定情况下，攻击者也许能够进行 HTTP 降级攻击，这会将 HTTPS 通信变为 HTTP通信，造成数据被明文传输。这是通过建立一个中间人代理并通过攻击者的主机来传输所有流量实现的，其中攻击者的主机并不含有用户的信息。然而，大部分现代的 web 浏览器、服务器以及 web 应用程序都对这种攻击作了防护。

### cURL for HTTPS

cURL should automatically handle all HTTPS communication standards and perform a secure handshake and then encrypt and decrypt data automatically. However, if we ever contact a website with an invalid SSL certificate or an outdated one, then cURL by default would not proceed with the communication to protect against the earlier mentioned MITM attacks:

&#x20; cURL 应自动地处理所有的 HTTPS 通信标准并进行安全握手，然后自动地加解密数据。然而，若我们用一个无效的或是过期的 SSL 证书与一个网站进行通信，那么 cURL 默认将不会继续处理数据以针对上述所提到的 MITM 攻击进行防护。

```bash
MirRoR4s@htb[/htb]$ curl https://inlanefreight.com

curl: (60) SSL certificate problem: Invalid certificate chain
More details here: https://curl.haxx.se/docs/sslcerts.html
...SNIP...
```

Modern web browsers would do the same, warning the user against visiting a website with an invalid SSL certificate.

现代的 web 浏览器也会进行同样的操作，并警告用户使用一个有效的 SSL 证书访问网站。

We may face such an issue when testing a local web application or with a web application hosted for practice purposes, as such web applications may not yet have implemented a valid SSL certificate. To skip the certificate check with cURL, we can use the `-k` flag:

&#x20; 当我们测试一个本地的 web 应用程序或是使用一个出于实操目的所托管的网站时，我们可能会遇到这个问题。因为这样的 web 应用程序也许还未能实现一个有效的 SSL 证书。为了在使用 cURL 时略过证书检查，我们可以使用 `-k` 选项。

```bash
MirRoR4s@htb[/htb]$ curl -k https://inlanefreight.com

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
...SNIP...
```

As we can see, the request went through this time, and we received the response data.

正如我们所看到的那样，这一次请求正常发送了，我们也收到了响应数据。
