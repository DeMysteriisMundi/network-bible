# Network Cheat Sheets

---

[TOC]

---

## General



### Organizations

***ISO*** - International Organization for Standardization.

***IEEE*** *(Institute of Electrical and Electronics Engineers)* - is a professional association for electronic engineering and electrical engineering. Its objectives are the educational and technical advancement of electrical and electronic engineering, telecommunications, computer engineering and allied disciplines.

---

### Standards

***IEEE 802*** - is a family of *IEEE* standards dealing with *Local Area Networks* and *Metropolitan Area Networks*. The services and protocols specified in *IEEE 802* mapped in the *Data Link* and *Physical Layers* of the *Seven-Layer OSI* networking reference model.

***IEEE 802.3*** - ...

***IEEE 802.2*** - ...

***IEEE 802.1Q*** (or *Dot1q*) - is the standard that supports *Virtual LANs* (or *VLANs*) on an *IEEE 802.3 Ethernet Network*. The standard defines a system of *VLAN Tagging* for *Ethernet Frames* and the accompanying procedures to be used by bridges and switches in handling such *Frames*. The standard also contains provisions for a *Quality-Of-Service* prioritization scheme commonly known as *IEEE 802.1p* and defines the *Generic Attribute Registration Protocol*.

***IEEE 802.1ad*** (or *QinQ*) - ...

---

### RFCs

...

---

## Basics



### Topologies

***Physical Topologies*** (*L1*) - it is how nodes are physically placed and connected.
***Logical Topologies*** (*L2/L3*) - it is how data goes in the physical topology.

#### Bus Topology

![bus-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/bus-topology.jpg)

**+**:

- Quick and simple to build.

**-**:

- At break the whole network will fall.

---

#### Ring Topology

![ring-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/ring-topology.jpg)

**+**:

- Quick and simple to build.
- More stable and reliable than *Bus Topology*.
- Possible to make reservation by second ring.

**-**:

- At break the whole network will fall.

---

#### Star Topology

![star-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/star-topology.jpg)

**+**:

- All nodes are connected to the one central node, that works as a repeater.
- More stable and reliable than *Bus Topology* and *Ring Topology*.
- At break the only one node will fall.

**-**:

- At break with the central node the whole network will fall.

---

#### Full-Mesh Topology

![full-mesh-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/full-mesh-topology.jpg)

**+**:

- The most reliable.

**-**:

- The most expensive.
- The hardest to build the big topology.
- The hardest to maintenance the big topology.

---

#### Partial-Mesh Topology

![partial-mesh-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/partial-mesh-topology.jpg)

**+**:

- Lightweight version of *Full-Mesh Topology*.

**-**:

- Expensive.
- Hard to build the big topology.
- Hard to maintenance the big topology.

---

#### Hybrid Topology

![hybrid-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/hybrid-topology.jpg)

**+/-**:

- Is a mix of previous topologies with their advantages and disadvantages.
- Beautiful.

---

### Network Architectures

#### Three-Tier Architecture

...

---

#### Leaf Spine

...

---

### Models

***OSI*** - Conceptual model of network protocols and standards used as a general model.
***TCP/IP*** - Conceptual model of network protocols and standards used as a practical model.

![tcp-ip-and-osi](/home/leschev/Projects/network-cheat-sheets/images/basics/models/tcp-ip-and-osi.jpg)

#### Physical

...

---

#### Data-link

...

---

#### Network

...

---

#### Transport

...

---

#### Session

...

---

#### Presentation

...

---

#### Application 

...

---

## Protocols, Standards and Mechanisms



### Physical Layer

...

---

### Data Link Layer

#### About Data Link Layer

*Data Link Layer* is responsible for data packaging before the sending the one. The data link layer has three main functions:

- It handles problems that occur as a result of bit transmission errors.
- It ensures data flows at a pace that doesn't overwhelm sending and receiving devices.
- It permits the transmission of data to Layer 3, the *Network Layer*, where it is addressed and routed.

*Data Link Layer* uses the *Frames* as a *Data Unit*. To transmit *Frames*, the switch uses a *Switching Table* (or *MAC Table*). Initially, after the switch is turned on, the table is empty. The switch fills it automatically when receiving *Frames* from the nodes. When the switch receives the *Frame* from the node, it first transfers it in accordance with its rules and then it remembers the sender's *MAC Address* in the *Frame* and maps it to the port on which it was received.

*IEEE 802.2* introduced separation of *Data Link Layer* to *MAC* and *LLC Sublayers*:

- *MAC (Media Access Control)* - Controls the access to media. Here it is set in which medium the frame is transmitted (*Token Ring*, *Ethernet*, *FDDI*).
- *LLC (Logical Link Control)* - Used for relations with *L3*. *LLC* frame may be of 3 types: *Informational*, *Managerial*, *Unnumbered*.

#### Switching process

There are four base *Switching State*:

- *Flooding*
- *Forwarding*
- *Filtering*
- *Learning*

*Flooding State* used when switch receives frame with *Unknown MAC Address* (or *Unknown Unicast Frame*). Switch transmit it to the all ports, so *Frame* reaches the destination node. Also *Flooding* used when switch receives *Multicast* or *Broadcast* *Frame*.

*Forwarding State* used when *Switching Table* contains record what port is located host with this *MAC Address*.

*Filtering State* used if the switch receives *Frame* through the known port, and the *Destination MAC Address* is accessible through the same port (that is, the switch discards the data). The switch believes that the node has already received this *Frame*, and does not duplicate it.

*Learning State* used if switch receives *Unknown Unicast Frame*. The switch recordings *MAC Address* the received *Frame* to  the *Switching Table*.

---

#### LLC

*LLC Frame Types* determined by procedures described by *IEEE 802.2*. There are 3 procedures:

- *LLC1* - without connection and confirmation. Errors are not corrected. Used with datagrams. This procedure uses *unnumbered* frames.
- *LLC2* - with connection and confirmation. Errors are corrected. This procedure uses all types of frames. Used in *NetBIOS*/*NetBEUI*, *LAP-D* protocols.
- *LLC3* - without connection but with confirmation. Used when high speed and knowledge of whether control information has reached the object is needed.

LLC header contains 3 fields:

|  DSAP  |  SSAP  | CONTROL |
| :----: | :----: | :-----: |
| 8 bits | 8 bits | 8 bits  |

- *DSAP* (*Destination Service Access Point*) - indicates protocol that gets the frame (on the receiving side).
- *SSAP* (*Source Service Access Point*) - indicates protocol that sends the frame (on the receiving side).
- *Control* - indicates if *connection-less* or *connection-oriented* frame.

---

#### LLC SNAP Extension

*LLC Header* allows to use only 128 of possible *L3 Protocols*. *SNAP (Subnetwork Access Protocol) Header* expands number of pointed protocols, for example, for any proprietary protocols.

![snap](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/snap.jpg)

*SNAP Header* contains 2 fields:

|  OUI   |  PID   |
| :----: | :----: |
| 8 bits | 8 bits |

- *OUI (Organizationally Unique Identifier)* - indicates organization identifier.
- *PID (Protocol ID)* - indicates *L3 Protocol*.

---

#### Token RIng

...

---

#### FDDI

...

---

#### Ethernet

There are several Ethernet frame types:

- *Ethernet II (IEEE 802.3)*
- *Ethernet LLC (IEEE 802.3/802.2)*
- *Ethernet LLC/SNAP (IEEE 802.3/802.2 SNAP)*

**Ethernet II**

![ethernet2](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet2.jpg)

*Ethernet II Frame* includes the next headers:

- *Preamble* - It's necessary for physics signal synchronization.
- *DA (Destination Address)* - MAC destination address.
- *SA (Source Address)* - MAC source address.
- *E-Type* - Type of *L3 Payload*.
- *Payload* - Encapsulated *L3 Packet*. If size < 46 bytes, then filled to 46 bytes. It required for correct *Collisions* identifying.
- *FCS (Frame Check System)* - Frame check system, codes of correction.

**Ethernet LLC**

![ethernet-llc](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet-llc.jpg)

Here *LLC Header* is added, described by *IEEE 802.2*.

*Ethernel LLC Frame* includes the next headers:

- *Preamble*
- *SFD (Sequence Frame Delimiter)* - Indicates about frame beginning.
- *DA*
- *SA*
- *Length* - length from this header to the end of frame.
- *LLC*
- *Payload*
- *FCS*

---

**Ethernet LLC/SNAP**

![ethernet-llc-snap](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet-llc-snap.jpg)

Here *SNAP Header* is added, described by *IEEE 802.2*.

*Ethernel LLC/SNAP Frame* includes the next headers:

- *Preamble*
- *SFD*
- *DA*
- *SA*
- *Length*
- *LLC*
- *SNAP*
- *Payload*
- *FCS* 

---

#### VLAN

***VLAN*** - is any *Broadcast Domain* that is partitioned and isolated in a *Computer Network* at the *Data Link Layer*. It allows to make devices invisible to each other even if they connected to the one switch or make their visible to each other if they connected to the different switches. *VLAN* is the main mechanism for creating a *Logical Network Topology* independent of its *Physical Topology* in the modern networks.

Tasks:

- Reducing the broadcast traffic in the network.
- Protection from the *ARP Spoofing*.

**Traffic Tagging**

The most common way to mark this is described in the *IEEE 802.1q*. There are also proprietary protocols that solve similar problems, for example, the *ISL Protocol* from *Cisco Systems*, but their popularity is much lower (and declining).

Mark added to frame by adding the special *Dot1q* header front of *EType Header* (in *IEEE 802.3*). This header contains 4 fields:

|  TPID   | Priority |  CFI  |   VID   |
| :-----: | :------: | :---: | :-----: |
| 16 bits |  3 bits  | 1 bit | 12 bits |

- *TPID (Tag Protocol Identifier)* - identifier of tag protocol. For Dot1q used value 0x8100.
- *Priority* - traffic priority.
- *CFI (Canonical Format Indicator)* - indicates to *MAC Address* format. 0 - canonical, 1 - non-canonical.
- *VID (VLAN Identifier)* - *VLAN* number.

**Access and Trunk ports**

There are 2 ports type:

- *Access* - tagging port
- *Trunk* - non-tagging port

*Access Port* links to terminal devices and transmits *Untagged Traffic*. It just removes tag when transmits frame to terminal device and adds tag when receives frame from terminal device. If *VLAN* not assigned to access port, then *Native VLAN* (default, but *Untagged VLAN*) is used.

*Trunk Port* links the network devices. This port doesn't removes the tag, it decides what have to do with received (from linked network device) frame based on frame tag. If frame is tagged and frame *VLAN* is equal to *Trunk Port VLAN*, then *Frame* will be transmitted on. *Untagged Frames* are discarded.

---

#### QinQ

**QinQ** - is a double *VLAN Tagging*, described by *IEEE 802.1ad*. Use the same fields as *IEEE 802.1q* standard. *QinQ* helps to decide several problems:

- *QinQ* expands number of *VLANs* from 4096 to 4096*4096
- *QinQ* using doesn't require to coordinate *VLAN* policy with *ISP* (*Internet Sevice Provider*). Your and *ISP's VLAN* policies will be separated. Your *VLAN Tag (Inner Tag)* will be encapsulated to *ISP's VLAN tag (Outer Tag)* and will be used only in your *LAN*. *ISP's VLAN Tag* will be used only in *ISP's LAN*. It looks like *VLAN Tunneling*. *ISP's VLAN Tag* creates the tunnel for yours *VLAN Traffic*.

*IEEE 802.1ad Tagging* looks like:

| Outer tag (ISP) | Inner tag (Your) |
| :-------------: | :--------------: |
|     4 bytes     |     24 bites     |

*QinQ* using requires the increasing of *MTU* (*Maximum Transmission Unit*) of more than 4 bytes.

---

### Network Layer

TODO: About Network Protocol

---

#### IPv4

[RFC791](https://tools.ietf.org/html/rfc791) - DARPA Internet Protocol Specification

![ipv4](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/network-layer/ip/ipv4.png)

*IPv4 Packet* includes the next headers:

- *Version* - IP protocol version. Has value 4 or 6.
- *IHL* (*Internet Header Length*) - Header length in *dword* (*32-bit words*). It indicates to beginning to *Payload* field.
- *DSCP* (*Differentiated Services Code Point*)
- *ECN* (*Explicit Congestion Notification*)
- *Length* - Packet length, including *Header* and *Payload*.
- *Identification* - Fragment identification.
- *Flags* - Fragmentation options.
- *Fragment Offset* - Fragment offset from the beginning.
- *TTL* (*Time To Live*) - In fact this value indicates to amount of intermediate nodes that packet can pass. Every node reduces the value by 1. When *TTL* will be equal to 0, packet will be discarded.
- *Protocol* - *L4* protocol.
- *CRC* (*Cyclic Redundancy Code*) - Correction codes.
- *Source IP Address*
- *Destination IP Address*
- *Parameters* - Debugging options.
- *Payload* - *L4 Payload*.

---

TODO: DSCP

---

TODO: ECN

---

**Fragmentation**

[RFC4459](https://tools.ietf.org/html/rfc4459) - MTU and Fragmentation Issues with In-The-Network Tunneling

If packet has a huge size, it's divided by several small-size fragments. This process named *Fragmentation*. Router compiles packet from the got fragments. *Fragmentation* process uses three fields:

- *Identification* - fragments of one packet have the same value. Router uses it to identify belonging to one packet.

- *Flags* - 3 bits: DF (*Don't Fragment*), MF (*More Fragments*) and reserved bit. *DF* bit forbids to fragment the packet. *MF* bit indicates that current fragment is not last of this packet. Router uses *MF* to identify beginning and ending of packet fragments set.

- *Fragment Offset* - Router uses it to identify the order of fragments in packet.

  *Fragmentation* is produced if packet size more then *MTU*. *MTU* (*Maximum Transmission Unit*) - is unit size, transmitted by *Ethernet Frame* (*Payload*). *IEEE 802.3* set size of *Ethernet Frame* in 1518 bytes. This chose based on different factors - network tasks, loading, transmitting data, distance etc. 18 bytes used for headers, except the *Preambula*. Don't forget about *LLC, SNAP, dot1q, qinq* that can add extra headers. The remaining 1500 bytes used for *Payload*. There are frames with size from 1500 to 16000 bytes - *Jumbo Frames*. They used in specific tasks.

---

**Parameters**

*Parameters* is optional header, that common used for a debugging information. This header consists of several fields of one of eight predefined types. In these fields, you can specify the exact route, register routers traveled by the packet, place security data or time stamps.

Since the number of fields in the *parameters* header can be arbitrary, several zero bytes must be added at the end of the header to align the packet header with a 32-bit boundary.

---

**IP Addresses**

[RFC5735](https://tools.ietf.org/html/rfc5735) - Special Use IPv4 Addresses
[RFC5737](https://tools.ietf.org/html/rfc5737) - IPv4 Address Blocks Reserved for Documentation
[RFC6306](https://tools.ietf.org/html/rfc6306) - Hierarchical IPv4 Framework
[RFC6890](https://tools.ietf.org/html/rfc6890) - Special-Purpose IP Address Registries

*IPv4 Address* consists of 32 bits. It's decided to represent the address by 4 octets in decimal notation as a numbers from 0 to 255 divided by dot. *IPv4 Address* consists of two parts: network number and host number. For differences network and host numbers *Subnet Mask* used.

```
181.3.25.103
```

*Subnet Mask* is bits mask, that consists of 32 bits, where in the beginning there are 1, followed by 0. *Subnet Mask* represented as well as *IPv4 Address*. Also it represented as a suffix with amount of 1.

```
255.255.0.0
```

or

```
x.x.x.x/16
```

There are several types of *IPv4 Casts*:

- *Unicast* - from node to the node.
- *Multicast* - from node to the node group.
- *Broadcast* - from node to every nodes.

There are two types of addresses:

- *Public (or white)* - accessible from Internet
- *Private (or gray)* - doesn't accessible from the *Internet*

*Private Addresses* depend on addressing type. There are two types of addressing:

- *Classful Addressing (deprecated)*
- *CIDR (Classless Inter-Domain Routing)*

---

**Classful Addressing**

[RFC1817](https://tools.ietf.org/html/rfc1817) - CIDR and Classful Routing

![classful-addressing](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/network-layer/ip/classful-addressing.png)

By *Classful Addressing* all the address space is divided to 5 classes:

- *A* - used for companies. 128 networks and 2 147 483 648  hosts
- *B* - used for companies. 16 384 networks and 1 073 741 824  hosts
- *C* - used for companies. 2 097 152 networks and 536 870 912 
- *D* - reserved network for multicast
- *E* - reserved network for experiments

Router distinguishes classes by first bits in the address. A - 0, B - 10, C - 110, D - 1110, E -1111. Router reads first bits until meet 0 or read four bits. By fact, this classful bits are immutable, so network address uses 32 - X - Y bits, where X is amount of classful bits and Y is amount of host bits.

*Classful Addressing* uses the next private addresses ranges:

- *100.64.0.0 - 100.127.255.255* - /10 subnet mask. Recommended by RFC 6598 for *CGN* (*Carrier-Grade NAT*).
- *172.16.0.0 - 172.31.255.255* - /12 subnet mask
- *192.168.0.0 - 192.168.255.255* - /16 subnet mask
- *127.0.0.0 - 127.255.255.255* - /8 subnet mask. Used for *Loopback Interfaces*.

---

**CIDR**

[RFC3021](https://tools.ietf.org/html/rfc3021) - Using 31-Bit Prefixes on IPv4 Point-to-Point Links
[RFC4632](https://tools.ietf.org/html/rfc4632) - Classless Inter-Domain Routing: The Internet Address Assignment and Aggregation Plan

***CIDR*** - IP addressing method that allows you to flexibly manage the IP address space without using the rigid framework of class addressing. Using this method allows you to economically use a limited resource of IP addresses, since it is possible to apply different subnet masks to different subnets. IP address is an array of bits. The subnet mask determines which bits in the IP address are the network address. The address block is set by specifying the starting address and subnet mask. Classless addressing is based on a *VLSM* (*Variable Length Subnet Mask*), while in class addressing, the length of the subnet mask had only 3 fixed values.

CIDR addressing uses the next private addresses ranges:

- *10.0.0.0 - 10.255.255.255* - /8 subnet mask

---

#### IPv6

[RFC2460](https://tools.ietf.org/html/rfc2460) - Internet Protocol, Version 6 Specification

*IPv6* is very different from the *IPv4*. In addition to increasing the size of the *IP Address* field, *IPv6* greatly optimizes the most of mechanisms. Look at *IPv6 Packet* structure:

![ipv6](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/network-layer/ip/ipv6.png)

*IPv6 Packet* contains the next headers:

- *Version*
- *Traffic Class*
- *Flow Label*
- *Payload Length*
- *Next Header*
- *Hop Limit*
- *Source IP Address*
- *Destination IP Address*

---

TODO: TRAFFIC CLASS

---

TODO: FLOW LABEL

---

**IPv6 Address**

[RFC2732](https://tools.ietf.org/html/rfc2732) - Format for Literal IPv6 Addresses in URL's
[RFC3484](https://tools.ietf.org/html/rfc3484) - Default Address Selection for Internet Protocol Version 6
[RFC3513](https://tools.ietf.org/html/rfc3513) - Internet Protocol Version 6 Addressing Architecture
[RFC3849](https://tools.ietf.org/html/rfc3849) - IPv6 Address Prefix Reserved for Documentation
[RFC4291](https://tools.ietf.org/html/rfc4291) - IP Version 6 Addressing Architecture
[RFC5952](https://tools.ietf.org/html/rfc5952) - A Recommendation for IPv6 Address Text Representation 

*IPv6 Address* contains from 128 bits, that are recorded in hexadecimal number system:

```
2001:0DB8:0000:3234:5678:9ABC:0000:0000/32
```

The parts of hexadecimal number divided by colon are named *hextets*. The long recording format *IPv6 Address* written above may lead to a short format. For this it is necessary to remove the leading zeros in the each address group. Groups containing only the zeros, need to be replaced by the one zero. The longest sequence consisting from the zeros replaced by two colons. The short recording format looks like:

```
2001:DB8:0:3234:5678:9ABC::/32
```

Pay attention to the number in the end of address, that follows by the slash symbol. It is the *Prefix* size. It is used like a subnet mask and divides the *IPv6 Address* by two parts:

- *Prefix* - The network address.
- *Interface Identifier* - The node address.

But *Prefix* also divided by two parts:

- *Global Routing Prefix* - The global network address.
- *Subnet Identifier* - The subnet address simplified.

*Global Routing Prefix* issues by provider. *Subnet Identifier* assigned by client. *IPv6* uses *CIDR* addressing and it is allows to use  *VLSM-like* mechanism - we can change subnet size by borrowing the low bits. But it recommends to changing 4 bits to avoid the situation when the one part of hexadecimal number indicates to subnet and the other part indicates to interface.

There are several *IPv6 Cast Types*:

- *Unicast* - From node to the node.
- *Anycast* - From node to the node from the *Multicast Group*.
- *Multicast* - From node to the node group.

---

**Unicast**

[RFC4193](https://tools.ietf.org/html/rfc4193) - Unique Local IPv6 Unicast Addresses
[RFC3587](https://tools.ietf.org/html/rfc3587) - IPv6 Global Unicast Address Format

IPv6 determines six types of *Unicast Addresses*:

- *Global Unicast Addresses*
- *Link-Local Addresses*
- *Loopback Address*
- *Unspecified Address*
- *Unique Local Addresses*
- *IPv4 Embedded Addresses*

*Global Unicast Addresses* are like *IPv4 Public Addresses*. They must be unique over the *Internet*. The range of these addresses is all addresses with the first three bits equal to "001". By the other words the first hextet is *2000* - *3FFF* range, except the *2001:0DB8::/32* that used for documentation.

*Link-Local Addresses* are addresses used in the local network. They are not routed. The range of such addresses is *FE80::/10*.

*Loopback Address* performs the same purpose as the *IPv4 Loopback Address*. The *IPv6 Loopback Address* is *::1/128*.

*Unspecified Address* is *0:0:0:0:0:0:0:0* or *::*. This address is not assigned to interface, but used as a source address when interface have not got the *Unicast Address*.

*Unique Local Addresses* are like *IPv4 Private Addresses*. They are used in the local network and they are routed unlike the *Link-Local Addresses*.

*IPv4 Embedded Addresses* are addresses of the form *::ffff:xxxx:xxxx* where *xxxx:xxxx* is the *IPv4 Address* recorded in hexadecimal. These addresses are used for devices that do not support IPv6 and provide a way to map the address space of the old version of the protocol to the address space of the new one.

---

**Multicast**

[RFC2375](https://tools.ietf.org/html/rfc2375) - IPv6 Multicast Address Assignments

Multicast IPv6 addresses are prefixed with *FF00::/8*. Multicast addresses can only be destination addresses, not source addresses. There are two types:

- Assigned Addresses - Special addresses whose purpose is predetermined.
- Solicited Addresses - Other addresses that used for applied purposes.

*Assigned Addresses* used by different devices groups:

- *FF02::1* - this group includes nodes from the local network.
- *FF02::2* - this group includes routers.
- *FF02::1:2* - this group includes *DHCPv6 servers.*

*Requested Addresses* created from *FF02::1:FF00:0/104* when interface uses *Unicast Address*. Last 24 bits is equal of 24 bits of *Unicast Address*. For example, interface with address *2001:0DB8:ABCD:0001:0000:0000:0123:A050* will receive traffic from the *FF02::1:FF23:A050*. *Requested Addresses* used by *NDP* (*Neighbor Discovery Protocol*) instead of *ARP*.

---

TODO: ARP

---

TODO: NDP

---

TODO: SLAAC

---

