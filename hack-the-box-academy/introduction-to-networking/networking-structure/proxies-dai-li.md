---
description: https://academy.hackthebox.com/module/34/section/300
---

# Proxies-代理

Many people have different opinions on what a proxy is:

许多人对于什么是代理有不同的意见：

* Security Professionals jump to `HTTP Proxies` (BurpSuite) or pivoting with a `SOCKS/SSH Proxy` (`Chisel`, `ptunnel`, `sshuttle`).
* 安全专家跳转到 HTTP 代理（BurpSuite）或利用 SOCKS/SSH 代理进行横向移动（Chisel、ptunnel、sshuttle）。
* Web Developers use proxies like Cloudflare or ModSecurity to block malicious traffic.
* Web 开发者使用类似于 Cloudflare 或 ModSecurity 的代理来阻塞恶意流量。
* Average people may think a proxy is used to obfuscate your location and access another country's Netflix catalog.
* 普通人可以会认为代理是用来混淆位置或访问其他国家的 Netflix 目录的。
* Law Enforcement often attributes proxies to illegal activity.
* 执法部门经常将代理归咎于非法活动。

Not all the above examples are correct. A proxy is when a device or service sits in the middle of a connection and acts as a mediator.&#x20;

上述举的例子并不都是正确的，代理就是一个位于连接的中间并充当中介者的设备或服务。

The `mediator` is the critical piece of information because it means the device in the middle must be able to inspect the contents of the traffic.&#x20;

中介者是重要的信息块，因为其意味着在中间的设备必须能够检查流量的内容。

Without the ability to be a `mediator`, the device is technically a `gateway`, not a proxy.

若不具备中介者的能力，该设备从技术上来说是一个网关而非代理。

Back to the above question, the average person has a mistaken idea of what a proxy is as they are most likely using a VPN to obfuscate their location, which technically is not a proxy.&#x20;

回到上述问题，普通人对于什么是代理有一个误解，因为他们也许会使用VPN来混淆他们的位置，但是这从技术上来说并不是代理。

Most people think whenever an IP Address changes, it is a proxy, and in most cases, it's probably best not to correct them as it is a common and harmless **misconception**.&#x20;

大部分人认为每当IP地址改变时，这就是一个代理。在大多数情况下，最好不要纠正他们，因为这是一个常见的但是无害的误解。

Correcting them could lead to a more extended conversation that trails into tabs vs. spaces, `emacs` vs. `vim`, or finding out they are a `nano` user.

纠正它们可能会导致更广泛的对话，例如制表符与空格、emacs 与 vim，或者发现他们是 nano 用户。

If you have trouble remembering this, proxies will almost always operate at Layer 7 of the OSI Model. There are many types of proxy services, but the key ones are:

如果您记不住这一点，代理几乎总是在 OSI 模型的第 7 层运行。代理服务有多种类型，但主要有：

* `Dedicated Proxy` / `Forward Proxy-专用代理/转发代理`
* `Reverse Proxy-反向代理`
* `Transparent Proxy-透明代理`

***

### Dedicated Proxy / Forward Proxy

The `Forward Proxy`, is what most people imagine a proxy to be. A Forward Proxy is when a client makes a request to a computer, and that computer carries out the request.

转发代理是大部分人想象中的代理。转发代理指的是客户端向某台计算机发起了请求，然后这台计算机执行该请求。

For example, in a corporate network, sensitive computers may not have direct access to the Internet. To access a website, they must go through a proxy (or web filter).&#x20;

举个例子，在一个组织的网络中，敏感的计算机也许不能够直接访问互联网。所以为了访问一个网站，这些计算机必须通过一个代理（或者是 web 过滤器）。

This can be an incredibly powerful line of defense against malware, as not only does it need to bypass the web filter (easy), but it would also need to be `proxy aware` or use a non-traditional C2 (a way for malware to receive tasking information).

这可能是针对恶意软件的极其强大的防线，因为它不仅需要绕过网络过滤器（简单），而且还需要代理感知或使用非传统的 C2（恶意软件接收的一种方式）任务信息）。

&#x20;If the organization only utilizes `FireFox`, the likelihood of getting proxy-aware malware is improbable.

如果组织仅使用 FireFox，则不太可能感染代理感知恶意软件。

Web Browsers like Internet Explorer, Edge, or Chrome all obey the "System Proxy" settings by default.&#x20;

默认情况下，Internet Explorer、Edge 或 Chrome 等 Web 浏览器都遵循“系统代理”设置。

If the malware utilizes WinSock (Native Windows API), it will likely be proxy aware without any additional code. Firefox does not use `WinSock` and instead uses `libcurl`, which enables it to use the same code on any operating system.&#x20;

如果恶意软件利用 WinSock（本机 Windows API），它可能无需任何额外代码即可识别代理。 Firefox 不使用 WinSock，而是使用 libcurl，这使得它能够在任何操作系统上使用相同的代码。

This means that the malware would need to look for Firefox and pull the proxy settings, which malware is highly unlikely to do.

这意味着恶意软件需要寻找 Firefox 并提取代理设置，而恶意软件大概率做不到这一点。

Alternatively, malware could use DNS as a c2 mechanism, but if an organization is monitoring DNS (which is easily done using [Sysmon](https://medium.com/falconforce/sysmon-11-dns-improvements-and-filedelete-events-7a74f17ca842) ), this type of traffic should get caught quickly.

或者，恶意软件可以使用 DNS 作为 c2 机制，但如果某个组织正在监视 DNS（使用 Sysmon 可以轻松完成），则这种类型的流量应该会很快会被捕获到。

Another example of a Forward Proxy is Burp Suite, as most people utilize it to forward HTTP Requests. However, this application is the swiss army knife of HTTP Proxies and can be configured to be a reverse proxy or transparent!

转发代理的另一个例子是 Burp Suite，因为大多数人使用它来转发 HTTP 请求。然而，这个应用程序是 HTTP 代理的瑞士军刀，可以被配置为反向代理或透明代理！

**Forward Proxy-转发代理示意图**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/forward\_proxy.png)

***

### Reverse Proxy

As you may have guessed, a `reverse proxy`, is the reverse of a `Forward Proxy`. Instead of being designed to filter outgoing requests, it filters incoming ones. The most common goal with a `Reverse Proxy`, is to listen on an address and forward it to a closed-off network.

Many organizations use CloudFlare as they have a robust network that can withstand most DDOS Attacks. By using Cloudflare, organizations have a way to filter the amount (and type) of traffic that gets sent to their webservers.

Penetration Testers will configure reverse proxies on infected endpoints. The infected endpoint will listen on a port and send any client that connects to the port back to the attacker through the infected endpoint. This is useful to bypass firewalls or evade logging. Organizations may have `IDS` (`Intrusion Detection Systems`), watching external web requests. If the attacker gains access to the organization over SSH, a reverse proxy can send web requests through the SSH Tunnel and evade the IDS.

Another common Reverse Proxy is `ModSecurity`, a `Web Application Firewall` (`WAF`). Web Application Firewalls inspect web requests for malicious content and block the request if it is malicious. If you want to learn more about this, we recommend reading into the [ModSecurity Core Rule Set](https://owasp.org/www-project-modsecurity-core-rule-set/), as its a great starting point. Cloudflare, also can act as a WAF but doing so requires letting them decrypt HTTPS Traffic, which some organizations may not want.

**Reverse Proxy**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/reverse\_proxy.png)

***

### (Non-) Transparent Proxy

All these proxy services act either `transparently` or `non-transparently`.

With a `transparent proxy`, the client doesn't know about its existence. The transparent proxy intercepts the client's communication requests to the Internet and acts as a substitute instance. To the outside, the transparent proxy, like the non-transparent proxy, acts as a communication partner.

If it is a `non-transparent proxy`, we must be informed about its existence. For this purpose, we and the software we want to use are given a special proxy configuration that ensures that traffic to the Internet is first addressed to the proxy. If this configuration does not exist, we cannot communicate via the proxy. However, since the proxy usually provides the only communication path to other networks, communication to the Internet is generally cut off without a corresponding proxy configuration.
