---
description: https://academy.hackthebox.com/module/34/section/301
---

# Networking Models

Two networking models describe the communication and transfer of data from one host to another, called `ISO/OSI model` and the `TCP/IP model`. This is a simplified representation of the so-called `layers` representing transferred Bits in readable contents for us.

有两种网络模型描述了从一台主机到另一台主机的通信和数据传输，称为 ISO/OSI 模型和 TCP/IP 模型。这是所谓的层的简化表示，其表示我们可读内容中传输的位。

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/net\_models4.png)

### The OSI Model

The `OSI` model, often referred to as `ISO/OSI` layer model, is a reference model that can be used to describe and define the communication between systems. The reference model has `seven` individual layers, each with clearly separated tasks.

OSI 模型，通常称为 ISO/OSI 层次模型，是一个可用于描述和定义系统间通信的参考模型。该参考模型有七个单独的层，每一层都有明确分离的任务。

The term `OSI` stands for `Open Systems Interconnection` model, published by the `International Telecommunication Union` (`ITU`) and the `International Organization for Standardization` (`ISO`). Therefore, the `OSI` model is often referred to as the `ISO/OSI` layer model.

OSI 一词代表开放系统互连模型，由国际电信联盟 (ITU) 和国际标准化组织 (ISO) 发布。因此，OSI 模型通常被称为 ISO/OSI 层模型。

### The TCP/IP Model

`TCP/IP` (`Transmission Control Protocol`/`Internet Protocol`) is a generic term for many network protocols. The protocols are responsible for the switching and transport of data packets on the Internet. The Internet is entirely based on the `TCP/IP` protocol family. However, `TCP/IP` does not only refer to these two protocols but is usually used as a generic term for an entire protocol family.

TCP/IP（传输控制协议/互联网协议）是许多网络协议的总称。这些协议负责互联网上数据包的交换和传输。 Internet 完全基于 TCP/IP 协议族。然而，TCP/IP 不仅指这两个协议，而且通常用作整个协议族的通用术语。

For example, `ICMP` (`Internet Control Message Protocol`) or `UDP` (`User Datagram Protocol`) belongs to the protocol family. The protocol family provides the necessary functions for transporting and switching data packets in a private or public network.

例如，ICMP（互联网控制消息协议）或UDP（用户数据报协议）就属于该协议族。该协议族提供了在专用或公共网络中传输和交换数据包的必要功能。

### ISO/OSI vs. TCP/IP

`TCP/IP` is a communication protocol that allows hosts to connect to the Internet. It refers to the `Transmission Control Protocol` used in and by applications on the Internet. In contrast to `OSI`, it allows a lightening of the rules that must be followed, provided that general guidelines are followed.

TCP/IP 是一种允许主机连接到 Internet 的通信协议。它指的是互联网上的应用程序使用的传输控制协议。与 OSI 相比，TCP/IP 减轻了要遵循的规则，而只遵循通用的规则。

`OSI`, on the other hand, is a communication gateway between the network and end-users. The OSI model is usually referred to as the reference model because it is older. It is also known for its strict protocol and limitations.

另一方面，OSI 是网络和终端用户之间的通信网关。 OSI 模型通常被称为参考模型，因为它较旧。它还以其严格的协议和限制而闻名。

### Packet Transfers

In a layered system, devices in a layer exchange data in a different format called a `protocol data unit` (`PDU`). For example, when we want to browse a website on the computer, the remote server software first passes the requested data to the application layer. It is processed layer by layer, each layer performing its assigned functions. The data is then transferred through the network's physical layer until the destination server or another device receives it. The data is routed through the layers again, with each layer performing its assigned operations until the receiving software uses the data.

在分层系统中，层中的设备以一种称为协议数据单元（PDU）的不同格式交换数据。例如，当我们要在计算机上浏览网站时，远程服务器软件首先将请求的数据传递给应用层。数据被逐层地处理，每一层执行其指定的功能。然后，通过物理层传输数据，直到目标服务器或某个设备接收到它。之后数据再次通过接收端的各层路由，每一层执行其分配的操作，直到接收软件（应用层）使用该数据。

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/net\_models\_pdu2.png)

During the transmission, each layer adds a `header` to the `PDU` from the upper layer, which controls and identifies the packet. This process is called `encapsulation`. The header and the data together form the PDU for the next layer. The process continues to the `Physical Layer` or `Network Layer`, where the data is transmitted to the receiver. The receiver reverses the process and unpacks the data on each layer with the header information. After that, the application finally uses the data. This process continues until all data has been sent and received.

在传输过程中，每一层都会在来自上层的 PDU 中添加一个报头，用于控制和识别数据包。这个过程称为封装。标头和数据一起构成下一层的 PDU。该过程持续到物理层或网络层，数据在此处传输到接收方。然后接收方逆转上述过程并使用报头信息解包每一层上的数据。最后应用层就可以使用解包完毕后的数据了。此过程将持续进行，直到所有数据均已发送和接收。

![image](https://academy.hackthebox.com/storage/modules/34/packet\_transfer.png)

For us, as penetration testers, both reference models are useful. With `TCP/IP`, we can quickly understand how the entire connection is established, and with `ISO`, we can take it apart piece by piece and analyze it in detail. This often happens when we can listen to and intercept specific network traffic. We then have to analyze this traffic accordingly, going into more detail in the `Network Traffic Analysis` module. Therefore, we should familiarize ourselves with both reference models and understand and internalize them in the best possible way.

作为渗透测试人员，这两个参考模型都很有用。使用 TCP/IP，可以快速了解整个连接是如何建立的，而使用 ISO 模型，可以拆开连接过程并进行详细的分析。通常在可以侦听和拦截特定的网络流量时，会发生这种情况。然后，我们必须相应地分析该流量，在网络流量分析模块中进行更详细的分析。因此，我们应该熟悉这两个参考模型，并以尽可能最好的方式理解和内化它们。
