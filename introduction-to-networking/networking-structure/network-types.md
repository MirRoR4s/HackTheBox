---
description: https://academy.hackthebox.com/module/34/section/298
---

# Network Types

Each network is structured differently and can be set up individually. For this reason, so-called `types` and `topologies` have been developed that can be used to categorize these networks. When reading about all the types of networks, it can be a bit of information overload as some network types include the geographical range. We rarely hear some of the terminologies in practice, so this section will be broken up into `Common Terms` and `Book Terms`. Book terms are good to know, as there has been a single documented case of an email server failing to deliver emails longer than 500 miles but don't be expected to be able to recite them on demand unless you are studying for a networking exam.

每个网络都有不同的结构，可以分别地建立这些网络。因此，人们提出了`类型`和`拓扑`来分类不同结构的网络。当尝试理解网络的所有类型时，我们可能会感到有点混乱，这是因为某些网络类型还包括了地理范围。我们在实践中很少听到一些术语，因此本节将分为通用术语和书籍术语。

**Common Terminology**

| **Network Type**                           | **Definition**                                            |
| ------------------------------------------ | --------------------------------------------------------- |
| Wide Area Network (WAN)-广域网                | Internet-因特网                                              |
| Local Area Network (LAN)-本地局域网             | Internal Networks (Ex: Home or Office)-内部网络（比如家或办公室）      |
| Wireless Local Area Network (WLAN)-无线本地局域网 | Internal Networks accessible over Wi-Fi-可通过 Wi-Fi 访问的内部网络 |
| Virtual Private Network (VPN)-虚拟专用网        | Connects multiple network sites to one `LAN`              |

***

### WAN

The WAN (Wide Area Network) is commonly referred to as `The Internet`. When dealing with networking equipment, we'll often have a WAN Address and LAN Address. The WAN one is the address that is generally accessed by the Internet. That being said, it is not inclusive to the Internet; a WAN is just a large number of LANs joined together. Many large companies or government agencies will have an "Internal WAN" (also called Intranet, Airgap Network, etc.). Generally speaking, the primary way we identify if the network is a WAN is to use a WAN Specific routing protocol such as BGP and if the IP Schema in use is not within RFC 1918 (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16).

广域网（Wide Area Network）通常也被称为**互联网**。网络设备通常会有一个 WAN 地址和一个 LAN 地址。WAN 一般是可通过互联网访问的地址，但是其实际上并不包含在互联网中，WAN 仅是大量的LANs连接起来构成的网络。许多大公司或政府机构都有一个内部的WAN（也被称为内联网，Airgap 网络等）。通常来说，判断某个网络是否是一个WAN的首要方法是利用特定的WAN路由协议，比如BGP。也可以通过查看使用的IP架构是否不在 RFC 1918内(10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16)来判断，如果不在那就是WAN。

### LAN / WLAN

LANs (Local Area Network) and WLANs (Wireless Local Area Network) will typically assign IP Addresses designated for local use (RFC 1918, 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16). In some cases, like some colleges or hotels, you may be assigned a routable (internet) IP Address from joining their LAN, but that is much less common. There's nothing different between a LAN or WLAN, other than WLAN's introduce the ability to transmit data without cables. It is mainly a security designation.

***

There are three main types `Virtual Private Networks` (`VPN`), but all three have the same goal of making the user feel as if they were plugged into a different network.

主要有三种不同类型的虚拟专用网VPN，但是这三类VPN的目标都是一样的即让用户感觉好像他们接入了不同的网络。

**Site-To-Site VPN**

Both the client and server are Network Devices, typically either `Routers` or `Firewalls`, and share entire network ranges. This is most commonly used to join company networks together over the Internet, allowing multiple locations to communicate over the Internet as if they were local.

对于此类VPN，客户端和服务端都是网络设备，通常不是路由器就是防火墙，它们共享整个网络范围。该类VPN最常被用于通过 Internet 将公司网络连接在一起，从而允许多个位置通过 Internet 进行通信，就像在本地一样。

**Remote Access VPN-远程访问 VPN**

This involves the client's computer creating a virtual interface that behaves as if it is on a client's network.&#x20;

远程访问 VPN 涉及到客户端的计算机创建了一个虚拟的接口，使得服务端看起来好像在客户端的网络中一样。

Hack The Box utilizes `OpenVPN`, which makes a TUN Adapter letting us access the labs.&#x20;

Hack The Box 利用了 `OpenVPN` 程序，该程序会制作一个 TUN 网络适配器以让我们访问实验室。

When analyzing these VPNs, an important piece to consider is the routing table that is created when joining the VPN.&#x20;

当分析这些 VPNs 时，要着重考虑的一点是路由表是在加入 VPN 时创建的。

If the VPN only creates routes for specific networks (ex: 10.10.10.0/24), this is called a `Split-Tunnel VPN`, meaning the Internet connection is not going out of the VPN.&#x20;

若 VPN 仅创建了特定网络的路由表（比如 10.10.10.0/24），那么就称该 VPN 为隧道分离 VPN，意思是因特网连接不出 VPN。

This is great for Hack The Box because it provides access to the Lab without the privacy concern of monitoring your internet connection.&#x20;

这一点对于 Hack The Box 来说特别好，因为这可以让我们访问到实验室，同时又没有互联网连接被监视的隐私忧虑。

However, for a company, `split-tunnel` VPN's are typically not ideal because if the machine is infected with malware, network-based detection methods will most likely not work as that traffic goes out the Internet.

然而，对于公司来说，隧道分离的 VPN's 通常并不理想。因为如果机器被恶意软件感染了，那么基于网络的识别方法很可能会失效，因为流量流出了互联网。



**SSL VPN**

This is essentially a VPN that is done within our web browser and is becoming increasingly common as web browsers are becoming capable of doing anything. Typically these will stream applications or entire desktop sessions to your web browser. A great example of this would be the HackTheBox Pwnbox.

SSL VPN 本质上是一种在浏览器中实现的VPN。随着 web 浏览器的功能更越来越多，SSL VPN 也变得越来越常见。通常，SSL VPN 会以流的形式将应用程序或整个桌面会话传输到 web 浏览器。 HackTheBox Pwnbox 就是一个很好的例子。

### Book Terms

<table><thead><tr><th width="309">Network Type</th><th>Definition</th></tr></thead><tbody><tr><td>Global Area Network (GAN)</td><td>Global network (the Internet)</td></tr><tr><td>Metropolitan Area Network (MAN)</td><td>Regional network (multiple LANs)</td></tr><tr><td>Wireless Personal Area Network (WPAN)</td><td>Personal network (Bluetooth)</td></tr></tbody></table>

**GAN**

A worldwide network such as the `Internet` is known as a `Global Area Network` (`GAN`). However, the Internet is not the only computer network of this kind. Internationally active companies also maintain isolated networks that span several `WAN`s and connect company computers worldwide. `GAN`s use the glass fibers infrastructure of wide-area networks and interconnect them by international undersea cables or satellite transmission.

**MAN**

`Metropolitan Area Network` (`MAN`) is a broadband telecommunications network that connects several `LAN`s in geographical proximity. As a rule, these are individual branches of a company connected to a `MAN` via leased lines. High-performance routers and high-performance connections based on glass fibers are used, which enable a significantly higher data throughput than the Internet. The transmission speed between two remote nodes is comparable to communication within a `LAN`.

Internationally operating network operators provide the infrastructure for `MAN`s. Cities wired as `Metropolitan Area Networks` can be integrated supra-regionally in `Wide Area Networks` (`WAN`) and internationally in `Global Area Networks` (`GAN`).

**PAN / WPAN**

Modern end devices such as smartphones, tablets, laptops, or desktop computers can be connected ad hoc to form a network to enable data exchange. This can be done by cable in the form of a `Personal Area Network` (`PAN`).

The wireless variant `Wireless Personal Area Network` (`WPAN`) is based on Bluetooth or Wireless USB technologies. A `wireless personal area network` that is established via Bluetooth is called `Piconet`. `PAN`s and `WPAN`s usually extend only a few meters and are therefore not suitable for connecting devices in separate rooms or even buildings.

In the context of the `Internet of Things` (`IoT`), `WPAN`s are used to communicate control and monitor applications with low data rates. Protocols such as Insteon, Z-Wave, and ZigBee were explicitly designed for smart homes and home automation.
