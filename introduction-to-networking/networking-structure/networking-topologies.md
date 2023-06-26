---
description: https://academy.hackthebox.com/module/34/section/299
---

# Networking Topologies

* 耐心！！！！

A `network topology` is a typical arrangement and `physical` or `logical` connection of devices in a network.&#x20;

网络拓扑是一个典型的排列，是网络中物理的或逻辑的设备间的连接。

Computers are `hosts`, such as `clients` and `servers`, that actively use the network.

计算机是主动使用网络的主机，比如客户端和服务器端。

&#x20;They also include `network components` such as `switches`, `bridges`, and `routers`, which we will discuss in more detail in later sections, which have a distribution function and ensure that all network hosts can establish a logical connection with each other.&#x20;

计算机也包括一些网络组件，比如交换机、网桥和路由器，这些组件具有分布式功能，可以确保所有的网络主机相互之间都可以建立逻辑的连接。在后面的章节我们会更详细的讨论这些组件。

The network topology determines the components to be used and the access methods to the transmission media.

网络拓扑决定了要使用的网络组件以及访问传输媒体的方法。

The `transmission medium layout` used to connect devices is the physical topology of the network.&#x20;

用于连接设备的传输媒体层是物理网络拓扑。

For conductive or glass fiber media, this refers to the cabling plan, the positions of the `nodes`, and the connections between the nodes and the cabling.&#x20;

对于导电的或是玻璃纤维的介质来说，这指的是布线方案、节点的位置以及节点和电缆之间的连接。

In contrast, the `logical topology` is how the signals act on the network media or how the data will be transmitted across the network from one device to the devices' physical connection.

相反地，逻辑拓扑是信号如何作用于网络介质或是数据如何通过网络从一个设备传递到另一个设备的物理连接。

We can divide the entire network topology area into three areas:

我们可将整个网络拓扑划分成如下三个区域：

**1. Connections**

| `Wired connections`        | `Wireless connections` |
| -------------------------- | ---------------------- |
| Coaxial cabling-同轴电缆       | Wi-Fi                  |
| Glass fiber cabling-玻璃纤维电缆 | Cellular-移动电话          |
| Twisted-pair cabling-双绞线   | Satellite-卫星           |
| and others-其他              | and others             |

***

**2. Nodes - Network Interface Controller (NICs)-节点-网卡**

|              |          |           |          |
| ------------ | -------- | --------- | -------- |
| Repeaters    | Hubs     | Bridges   | Switches |
| Router/Modem | Gateways | Firewalls |          |

Network nodes are the `transmission medium's connection points` to transmitters and receivers of electrical, optical, or radio signals in the medium.&#x20;

网络节点就是到电路、光纤或无线电信号的发送端和接收端的传输介质连接点

A node may be connected to a computer, but certain types may have only one microcontroller on a node or may have no programmable device at all.

节点可能会连接到一台计算机上，但某些类型的节点上可能只有一个微控制器，或者根本没有可编程设备。

**3. Classifications**

We can imagine a topology as a virtual form or `structure of a network`.&#x20;

我们可以将拓扑想象成一个虚拟的表格或是网络的结构。

This form does not necessarily correspond to the actual physical arrangement of the devices in the network.&#x20;

这个表格没有必要对应于网络中设备的实际的物理排列。

Therefore these topologies can be either `physical` or `logical`.

所以这些拓扑可以是物理的或是逻辑的。

&#x20;For example, the computers on a `LAN` may be arranged in a circle in a bedroom, but it is very unlikely to have an actual ring topology.

举个例子，LAN 中的计算机也许会被排列成圆形，但它在实际中大概率不会有一个环形的拓扑。

Network topologies are divided into the following eight basic types:

网络拓扑可被分成以下 8 种基本的类型：

|                    |             |
| ------------------ | ----------- |
| Point-to-Point-点对点 | Bus-总线型     |
| Star-星型            | Ring-环型     |
| Mesh-网状型           | Tree-树型     |
| Hybrid-混合型         | Daisy Chain |

More complex networks can be built as hybrids of two or more of the basic topologies mentioned above.

根据两个或多个上述的拓扑，可将这些拓扑混合起来以构造更加复杂的网络。

***

### Point-to-Point

The simplest network topology with a dedicated connection between two hosts is the `point-to-point` topology. In this topology, a direct and straightforward physical link exists only between `two hosts`. These two devices can use these connections for mutual communication.

`Point-to-point` topologies are the basic model of traditional telephony and must not be confused with `P2P` (`Peer-to-Peer` architecture).

**Point-To-Point Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_p2p.png)

***

### Bus

All hosts are connected via a transmission medium in the bus topology. Every host has access to the transmission medium and the signals that are transmitted over it. There is no central network component that controls the processes on it. The transmission medium for this can be, for example, a `coaxial cable`.

Since the medium is shared with all the others, only `one host can send`, and all the others can only receive and evaluate the data and see whether it is intended for itself.

**Bus Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_bus.png)

***

### Star

The star topology is a network component that maintains a connection to all hosts. Each host is connected to the `central network component` via a separate link. This is usually a router, a hub, or a switch. These handle the `forwarding function` for the data packets. To do this, the data packets are received and forwarded to the destination. The data traffic on the central network component can be very high since all data and connections go through it.

**Star Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_star.png)

***

### Ring

The `physical` ring topology is such that each host or node is connected to the ring with two cables:

* One for the `incoming` signals and
* the another for the `outgoing` ones.

This means that one cable arrives at each host and one cable leaves. The ring topology typically does not require an active network component. The control and access to the transmission medium are regulated by a protocol to which all stations adhere.

A `logical` ring topology is based on a physical star topology, where a distributor at the node simulates the ring by forwarding from one port to the next.

The information is transmitted in a predetermined transmission direction. Typically, the transmission medium is accessed sequentially from station to station using a retrieval system from the central station or a `token`. A token is a bit pattern that continually passes through a ring network in one direction, which works according to the `claim token process`.

**Ring Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_ring.png)

***

### Mesh

Many nodes decide about the connections on a `physical` level and the routing on a `logical` level in meshed networks. Therefore, meshed structures have no fixed topology. There are two basic structures from the basic concept: the `fully meshed` and the `partially meshed` structure.

Each host is connected to every other host in the network in a `fully meshed structure`. This means that the hosts are meshed with each other. This technique is primarily used in `WAN` or `MAN` to ensure high reliability and bandwidth.

In this setup, important network nodes such as routers could be networked together. If one router fails, the others can continue to work without problems, and the network can absorb the failure due to the many connections.

Each node of a fully meshed topology has the same routing functions and knows the neighboring nodes it can communicate with proximity to the network gateway and traffic loads.

In the `partially meshed structure`, the endpoints are connected by only one connection. In this type of network topology, specific nodes are connected to exactly one other node, and some other nodes are connected to two or more other nodes with a point-to-point connection.

**Mesh Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_mesh.png)

***

### Tree

The tree topology is an extended star topology that more extensive local networks have in this structure. This is especially useful when several topologies are combined. This topology is often used, for example, in larger company buildings.

There are both logical tree structures according to the `spanning tree` and physical ones. Modular modern networks, based on structured cabling with a hub hierarchy, also have a tree structure. Tree topologies are also used for `broadband networks` and `city networks` (`MAN`).

**Tree Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_tree.png)

***

### Hybrid

Hybrid networks combine two or more topologies so that the resulting network does not present any standard topologies. For example, a tree network can represent a hybrid topology in which star networks are connected via interconnected bus networks. However, a tree network that is linked to another tree network is still topologically a tree network. A hybrid topology is always created when `two different` basic network topologies are interconnected.

**Hybrid Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_hybrid.png)

***

### Daisy Chain

In the daisy chain topology, multiple hosts are connected by placing a cable from one node to another.

Since this creates a chain of connections, it is also known as a daisy-chain configuration in which multiple hardware components are connected in a series. This type of networking is often found in automation technology (`CAN`).

Daisy chaining is based on the physical arrangement of the nodes, in contrast to token procedures, which are structural but can be made independent of the physical layout. The signal is sent to and from a component via its previous nodes to the computer system.

**Daisy Chain Topology**

![image](https://academy.hackthebox.com/storage/modules/34/redesigned/topo\_daisy-chain.png)

