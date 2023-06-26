---
description: https://academy.hackthebox.com/module/34/section/303
---

# The TCP/IP Model

The `TCP/IP` model is also a layered reference model, often referred to as the `Internet Protocol Suite`. The term `TCP/IP` stands for the two protocols `Transmission Control Protocol` (`TCP`) and `Internet Protocol` (`IP`). `IP` is located within the `network layer` (`Layer 3`) and `TCP` is located within the `transport layer` (`Layer 4`) of the `OSI` layer model.

TCP/IP 模型也是一个分层参考模型，通常被称为 Internet 协议簇。术语 TCP/IP 代表传输控制协议 (TCP) 和互联网协议 (IP) 这两个协议。 IP 位于 OSI 层模型的网络层（第 3 层），TCP 位于 OSI 层模型的传输层（第 4 层）。

<table data-header-hidden><thead><tr><th width="237"></th><th></th></tr></thead><tbody><tr><td><strong>Layer</strong></td><td><strong>Function</strong></td></tr><tr><td><code>4.Application-应用层</code></td><td>The Application Layer allows applications to access the other layers' services and defines the protocols applications use to exchange data.-应用层允许应用程序访问其他层的服务并定义应用程序用于交换数据的协议。</td></tr><tr><td><code>3.Transport-传输层</code></td><td>The Transport Layer is responsible for providing (TCP) session and (UDP) datagram services for the Application Layer.-传输层负责为应用层提供（TCP）会话和（UDP）数据报服务。</td></tr><tr><td><code>2.Internet-网络层</code></td><td>The Internet Layer is responsible for host addressing, packaging, and routing functions.-互联网层负责主机寻址、打包和路由功能。</td></tr><tr><td><code>1.Link-链路层</code></td><td>The Link layer is responsible for placing the TCP/IP packets on the network medium and receiving corresponding packets from the network medium. TCP/IP is designed to work independently of the network access method, frame format, and medium.-链路层负责将 TCP/IP 数据包放置在网络介质上并从网络介质接收相应的数据包。 TCP/IP 被设计为独立于网络访问方法、帧格式和介质而工作。</td></tr></tbody></table>

***

With `TCP/IP`, every application can transfer and exchange data over any network, and it does not matter where the receiver is located. `IP` ensures that the data packet reaches its destination, and `TCP` controls the data transfer and ensures the connection between data stream and application. The main difference between `TCP/IP` and `OSI` is the number of layers, some of which have been combined.

通过 TCP/IP，每个应用程序可在任意网络上传输和交换数据，并且无论接收者位于何处。 IP 都确保数据包能够到达目的地。TCP 控制数据传的输并确保数据流和应用程序之间的连接。 TCP/IP 和 OSI 之间的主要区别在于层数，其中一些已合并。

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/net\_models4.png)

The most important tasks of `TCP/IP` are:

TCP/IP 最重要的任务是：

<table data-header-hidden><thead><tr><th width="255"></th><th width="113.33333333333331"></th><th></th></tr></thead><tbody><tr><td><strong>Task</strong></td><td><strong>Protocol</strong></td><td><strong>Description</strong></td></tr><tr><td><code>Logical Addressing-逻辑地址</code></td><td><code>IP</code></td><td>Due to many hosts in different networks, there is a need to structure the network topology and logical addressing. Within TCP/IP, IP takes over the logical addressing of networks and nodes. Data packets only reach the network where they are supposed to be. The methods to do so are <code>network classes</code>, <code>subnetting</code>, and <code>CIDR</code>.-由于不同网络中有许多主机，因此需要构建网络拓扑和逻辑寻址。在 TCP/IP 中，IP 接管网络和节点的逻辑寻址。数据包仅到达它们应该到达的网络。实现此目的的方法是网络类别、子网划分和 CIDR。</td></tr><tr><td><code>Routing-路由</code></td><td><code>IP</code></td><td>For each data packet, the next node is determined in each node on the way from the sender to the receiver. This way, a data packet is routed to its receiver, even if its location is unknown to the sender.-对于每个数据包，在从发送方到接收方途中的每个节点中确定下一个节点。这样，即使发送者不知道数据包的位置，数据包也会被路由到接收者。</td></tr><tr><td><code>Error &#x26; Control Flow</code></td><td><code>TCP</code></td><td>The sender and receiver are frequently in touch with each other via a virtual connection. Therefore control messages are sent continuously to check if the connection is still established.-发送者和接收者经常通过虚拟连接相互联系。因此，控制消息会不断发送以检查连接是否仍然建立。</td></tr><tr><td><code>Application Support-应用程序支持</code></td><td><code>TCP</code></td><td>TCP and UDP ports form a software abstraction to distinguish specific applications and their communication links.-TCP 和 UDP 端口形成了软件抽象来区分特定应用程序及其通信链路。</td></tr><tr><td><code>Name Resolution-名字解析</code></td><td><code>DNS</code></td><td>DNS provides name resolution through Fully Qualified Domain Names (FQDN) in IP addresses, enabling us to reach the desired host with the specified name on the internet.-DNS 通过 IP 地址中的完全限定域名 (FQDN) 提供名称解析，使我们能够到达互联网上具有指定名称的期望主机。</td></tr></tbody></table>
