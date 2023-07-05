---
description: https://academy.hackthebox.com/module/34/section/302
---

# The OSI Model

The goal in defining the `ISO/OSI` standard was to create a reference model that enables the communication of different technical systems via various devices and technologies and provides compatibility. The `OSI` model uses `seven` different layers, which are hierarchically based on each other to achieve this goal. These layers represent phases in the establishment of each connection through which the sent packets pass. In this way, the standard was created to trace how a connection is structured and established visually.

定义 ISO/OSI 标准的目标是创建一个参考模型，使不同技术系统能够通过各种设备和技术进行通信并提供兼容性。 OSI 模型分为 7 层，这些层在层次上相互基于以实现这一目标。这些层代表发送数据包所经过的每个连接建立过程中的阶段。通过这种方式，创建了标准来跟踪如何以可视地方式构建和建立连接。

<table data-header-hidden><thead><tr><th width="235"></th><th></th></tr></thead><tbody><tr><td><strong>Layer</strong></td><td><strong>Function</strong></td></tr><tr><td><code>7.Application-应用层</code></td><td>Among other things, this layer controls the input and output of data and provides the application functions.-该层控制数据的输入和输出并提供应用程序功能。</td></tr><tr><td><code>6.Presentation-表示层</code></td><td>The presentation layer's task is to transfer the system-dependent presentation of data into a form independent of the application.-表示层的任务是将依赖于系统的数据表示转换为独立于应用程序的形式。</td></tr><tr><td><code>5.Session-会话层</code></td><td>The session layer controls the logical connection between two systems and prevents, for example, connection breakdowns or other problems.-会话层控制两个系统之间的逻辑连接并防止例如连接故障或者是其他的问题。</td></tr><tr><td><code>4.Transport-传输层</code></td><td>Layer 4 is used for end-to-end control of the transferred data. The Transport Layer can detect and avoid congestion situations and segment data streams.-第 4 层用于传输数据的端到端控制。传输层可以检测并避免拥塞的情况并对数据流进行分段。</td></tr><tr><td><code>3.Network-网络层</code></td><td>On the networking layer, connections are established in circuit-switched networks, and data packets are forwarded in packet-switched networks. Data is transmitted over the entire network from the sender to the receiver.-在网络层，连接是在电路交换网中建立的，然而数据包的转发是在分组交换网络中进行的。数据通过整个网络从发送方传输到接收方。</td></tr><tr><td><code>2.Data Link-数据链路层</code></td><td>The central task of layer 2 is to enable reliable and error-free transmissions on the respective medium. For this purpose, the bitstreams from layer 1 are divided into blocks or frames.-第 2 层的中心任务是在相应介质上实现可靠且无差错的传输。为此，来自第 1 层的比特流被分为块或帧。</td></tr><tr><td><code>1.Physical-物理层</code></td><td>The transmission techniques used are, for example, electrical signals, optical signals, or electromagnetic waves. Through layer 1, the transmission takes place on wired or wireless transmission lines.-物理层所用的传输技术有电信号、光信号或电磁波。通过第一层，在有线或无线传输线上进行数据的传输</td></tr></tbody></table>



The layers `2-4` are `transport oriented`, and the layers `5-7` are `application oriented` layers. In each layer, precisely defined tasks are performed, and the interfaces to the neighboring layers are precisely described. Each layer offers services for use to the layer directly above it. To make these services available, the layer uses the services of the layer below it and performs the tasks of its layer.

第 2-4 层是面向传输的层，第 5-7 层是面向应用的层。在每一层中，都要执行精确定义的任务，并且精确描述相邻层的接口。每一层都直接地向其上层提供服务。为了使这些服务可用，各层要使用下层提供的服务然后执行本层的任务。

If two systems communicate, all seven layers of the `OSI` model are run through at least `twice`, since both the sender and the receiver must take the layer model into account. Therefore, a large number of different tasks must be performed in the individual layers to ensure the communication's security, reliability, and performance.

如果两个系统进行通信，则 OSI 模型的所有七层都至少运行两次，因为发送方和接收方都必须考虑分层模型。因此，必须在各个层中执行大量不同的任务，以确保通信的安全性、可靠性和性能。

When an application sends a packet to the other system, the system works the layers shown above from layer `7` down to layer `1`, and the receiving system unpacks the received packet from layer `1` up to layer `7`.

当应用程序将数据包发送到另一个系统时，系统将按照上面所示从第 7 层到第 1 层的对数据包进行封装，接收系统将接收到的数据包从第 1 层到第 7 层进行解包。\
