# Network Cheat Sheets

---

[TOC]

---

## General



### Organizations

**ISO** - International Organization for Standardization.
More: https://en.wikipedia.org/wiki/International_Organization_for_Standardization

**IEEE** *(Institute of Electrical and Electronics Engineers)* - is a professional association for electronic engineering and electrical engineering. Its objectives are the educational and technical advancement of electrical and electronic engineering, telecommunications, computer engineering and allied disciplines.
More: https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers

---

### Standards

**IEEE 802** - is a family of IEEE standards dealing with *local area networks* and *metropolitan area networks*. The services and protocols specified in IEEE 802 map to the Data Link and Physical layers of the seven-layer OSI networking reference model.
More: https://en.wikipedia.org/wiki/IEEE_802

**IEEE 802.3** - ...

**IEEE 802.2** - ...

**IEEE 802.1Q** (or *Dot1q*) - is the networking standard that supports *virtual LANs* (or *VLANs*) on an IEEE 802.3 Ethernet network. The standard defines a system of *VLAN tagging* for Ethernet frames and the accompanying procedures to be used by bridges and switches in handling such frames. The standard also contains provisions for a quality-of-service prioritization scheme commonly known as IEEE 802.1p and defines the Generic Attribute Registration Protocol.
More: http://xgu.ru/wiki/802.1Q

**IEEE 802.1AD** (or *QinQ*) - ...

---

## Basics



### Topologies

**Physical Topologies** (*L1*) - it is how nodes are physically placed and connected.
**Logical Topologies** (*L2/L3*) - it is how data goes in the physical topology.

#### Bus Topology

![bus-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/bus-topology.jpg)

**+**:

- quick and simple to build

**-**:

- at break the whole network will fall

---

#### Ring Topology

![ring-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/ring-topology.jpg)

**+**:

- quick and simple to build
- more stable and reliable than *Bus Topology*
- possible to make reservation by second ring

**-**:

- at break the whole network will fall

---

#### Star Topology

![star-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/star-topology.jpg)

**+**:

- all nodes are connected to the one central node, that works as a repeater 
- more stable and reliable than *Bus Topology* and *Ring Topology*
- at break the only one node will fall

**-**:

- at break with the central node the whole network will fall

---

#### Full-Mesh Topology

![full-mesh-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/full-mesh-topology.jpg)

**+**:

- the most reliable

**-**:

- the most expensive
- the hardest to build the big topology
- the hardest to maintenance the big topology

---

#### Partial-Mesh Topology

![partial-mesh-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/partial-mesh-topology.jpg)

**+**:

- lightweight version of *Full-Mesh Topology*

**-**:

- expensive
- hard to build the big topology
- hard to maintenance the big topology

---

#### Hybrid Topology

![hybrid-topology](/home/leschev/Projects/network-cheat-sheets/images/basics/topologies/hybrid-topology.jpg)

**+/-**:

- is a mix of previous topologies with their advantages and disadvantages
- beautiful

---

### Network Architectures

#### Three-tier architecture

...

---

#### Leaf Spine

...

---

### Models

**OSI** - conceptual model of network protocols and standards used as a general model.
**TCP/IP** - conceptual model of network protocols and standards used as a practical model.

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

More: http://xgu.ru/wiki/%D0%A1%D0%B5%D1%82%D0%B5%D0%B2%D0%B0%D1%8F_%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D1%8C_OSI

---

## Protocols, Standards and Mechanisms



### Physical Layer

...

---

### Data Link Layer

#### About Data Link Layer

Data Link layer uses *frames* as a *data unit*. *IEEE 802.2* introduced separation of Data Link layer to *MAC* and *LLC* sublayers:

- MAC (*Media Access Control*) - controls the access to media. Here it is set in which medium the frame is transmitted (*Token Ring*, *Ethernet*, *FDDI*).
- LLC (*Logical Link Control*) - used for relations with L3. LLC frame may be of 3 types: *informational*, *managerial*, *unnumbered*.

**LLC**

LLC frame types determined by procedures described by *IEEE 802.2*. There are 3 procedures:

- LLC1 - without connection and confirmation. Errors are not corrected. Used with datagrams. This procedure uses *unnumbered* frames.
- LLC2 - with connection and confirmation. Errors are corrected. This procedure uses all types of frames. Used in *NetBIOS*/*NetBEUI*, *LAP-D* protocols.
- LLC3 - without connection but with confirmation. Used when high speed and knowledge of whether control information has reached the object is needed.

LLC header contains 3 fields:

|  DSAP  |  SSAP  | CONTROL |
| :----: | :----: | :-----: |
| 8 bits | 8 bits | 8 bits  |

- DSAP (*Destination Service Access Point*) - indicates protocol that gets the frame (on the receiving side)
- SSAP (*Source Service Access Point*) - indicates protocol that sends the frame (on the receiving side)
- Control - indicates if *connection-less* or *connection-oriented* frame

---

**LLC SNAP Extension**

LLC header allows to use only 128 of possible L3 protocols. *SNAP* (*Subnetwork Access Protocol*) header expands number of pointed protocols, for exam	ple, for any proprietary protocols.

![snap](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/snap.jpg)

SNAP header contains 2 fields:

|  OUI   |  PID   |
| :----: | :----: |
| 8 bits | 8 bits |

- OUI (*Organizationally Unique Identifier*) - indicates organization identifier
- PID (*Protocol ID*) - indicates L3 protocol

---

#### Switching Principle

To transmit frames, the switch uses a switching table (or *MAC table*). Initially, after the switch is turned on, the table is empty. The switch fills it automatically when receiving frames from the hosts. When the switch receives the frame from the host, it first transfers it in accordance with its rules (described below), and then it remembers the sender's MAC address in the frame and maps it to the port on which it was received.

**Base Mechanisms**

Switch uses four base mechanisms to frame transmitting:

- Flooding
- Forwarding
- Filtering
- Learning

*Flooding* mechanism used when switch receives frame with unknown *MAC* address (*unknown unicast frame*). Switch transmit it to all ports, so frame reaches the destination host. Also *Flooding* used when switch receives *multicast* or *broadcast* frame.

*Forwarding* mechanism used when switching table contains record what port is located host with this *MAC* address.

*Filtering* mechanism used if the switch receives frame through the specified port, and the destination *MAC* address is accessible through the same port (that is, the switch discards the data). The switch believes that the host has already received this frame, and does not duplicate it.

*Learning* mechanism used if switch receives *unknown unicast frame*. The switch recordings *MAC* address the received frame to switching table.

More: http://xgu.ru/wiki/VLAN#.D0.9F.D1.80.D0.B8.D0.BD.D1.86.D0.B8.D0.BF.D1.8B_.D1.80.D0.B0.D0.B1.D0.BE.D1.82.D1.8B_.D0.BA.D0.BE.D0.BC.D0.BC.D1.83.D1.82.D0.B0.D1.82.D0.BE.D1.80.D0.B0

---

#### Token RIng

...

---

#### FDDI

...

---

#### Ethernet

There are several Ethernet frame types:

- Ethernet II (IEEE 802.3)
- Ethernet LLC (IEEE 802.3/802.2)
- Ethernet LLC/SNAP (IEEE 802.3/802.2 SNAP)

**Ethernet II**

![ethernet2](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet2.jpg)

Ethernet II frame includes the next headers:

- Preamble - it's necessary for physics signal synchronization
- DA (*Destination Address*) - MAC destination address
- SA (*Source Address*) - MAC source address
- E-Type - type of L3 payload
- Payload - encapsulated L3 packet. If size < 46 bytes, then filled to 46 bytes. It required for correct collisions identifying.
- FCS (*Frame Check System*) - frame check system, codes of correction

**Ethernet LLC**

![ethernet-llc](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet-llc.jpg)

Here *LLC* header is added, described by IEEE 802.2.

Ethernel LLC frame includes the next headers:

- Preamble
- SFD (*Sequence Frame Delimiter*) - Indicates about frame beginning
- DA
- SA
- Length - length from this header to the end of frame
- LLC
- Payload
- FCS

---

**Ethernet LLC/SNAP**

![ethernet-llc-snap](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/data-link-layer/ethernet/ethernet-llc-snap.jpg)

Here *SNAP* header is added, described by IEEE 802.2.

Ethernel LLC/SNAP frame includes the next headers:

- Preamble
- SFD
- DA
- SA
- Length
- LLC
- SNAP
- Payload
- FCS 

---

#### VLAN

**VLAN** - is any broadcast domain that is partitioned and isolated in a computer network at the data link layer. It allows to make devices invisible to each other even if they connected to the one switch or make their visible to each other if they connected to the different switches. VLAN is the main mechanism for creating a logical network topology independent of its physical topology in the modern networks.

Tasks:

- reducing the broadcast traffic in the network
- protection from the *ARP Spoofing*

**Traffic Tagging**

The most common way to mark this is described in the open IEEE 802.1Q standard. There are also proprietary protocols that solve similar problems, for example, the *ISL* protocol from *Cisco Systems*, but their popularity is much lower (and declining).

Mark added to frame by adding the special *Dot1q* header front of *EType* header (in Ethernet II standard). This header contains 4 fields:

|  TPID   | Priority |  CFI  |   VID   |
| :-----: | :------: | :---: | :-----: |
| 16 bits |  3 bits  | 1 bit | 12 bits |

- TPID (*Tag Protocol Identifier*) - identifier of tag protocol. For Dot1q used value 0x8100.
- Priority - traffic priority
- CFI (*Canonical Format Indicator*) - indicates to MAC address format. 0 - canonical, 1 - non-canonical.
- VID (*VLAN Identifier*) - VLAN number

**Access and Trunk ports**

There are 2 ports type:

- Access - tagging port
- Trunk - non-tagging port

Access port links to terminal devices and transmits untagged traffic. It just removes tag when transmits frame to terminal device and adds tag when receives frame from terminal device. If VLAN not assigned to access port, then *Native VLAN* (default, but untagged VLAN) is used.

Trunk port links the network devices. This port doesn't removes the tag, it decides what have to do with received (from linked network device) frame based on frame tag. If frame is tagged and frame VLAN is equal to trunk port VLAN, then frame will be transmitted on. Untagged frames are discarded.

More: http://xgu.ru/wiki/VLAN

---

#### QinQ

**QinQ** - is a double VLAN tagging, described by *IEEE 802.1AD* standard. Use the same fields as *IEEE 802.1Q* standard. *QinQ* helps to decide several problems:

- *QinQ* expands number of VLANs from 4096 to 4096*4096
- *QinQ* using doesn't require to coordinate VLAN policy with *ISP* (*Internet Sevice Provider*). Your and ISP's VLAN policies will be separated. Your VLAN tag (*inner tag*) will be encapsulated to ISP's VLAN tag (*outer tag*) and will be used only in your LAN. ISP's VLAN tag will be used only in ISP's LAN. It looks like VLAN tunneling. ISP's VLAN tag creates the tunnel for yours VLAN traffic.

*IEEE 802.1AD* tagging looks like:

| Outer tag (ISP) | Inner tag (Your) |
| :-------------: | :--------------: |
|     4 bytes     |     24 bites     |

*QinQ* using requires the increasing of *MTU* (*Maximum Transmission Unit*) of more than 4 bytes.

More: https://en.wikipedia.org/wiki/IEEE_802.1ad

---

### Network Layer

#### About Network Layer

...

#### Internet Protocol

**IP** (*Internet Protocol*) - is the routable protocol whose main purpose are internetworking and essentially establishes the Internet. *IP* combines network segments into a single network, ensuring the delivery of data packets between any network nodes through an arbitrary number of intermediate nodes (*routers*).

There are two versions of *IP*:

- IPv4
- IPv6

**IPv4**

![ipv4](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/network-layer/ip/ipv4.png)

IPv4 packet includes the next headers:

- Version - IP protocol version. Has value 4 or 6.
- IHL (*Internet Header Length*) - Header length in *dword* (*32-bit words*). It indicates to beginning of *payload*.
- DSCP (*Differentiated Services Code Point*)
- ECN (*Explicit Congestion Notification*)
- Length - packet length, including headers and payload
- Identification
- Flags
- Fragment Offset
- TTL (*Time To Live*) - In fact this value indicates to amount of intermediate nodes that packet can pass. Every node reduces the value by 1. When *TTL* will be equal to 0, packet will be discarded.
- Protocol - *L4* protocol
- CRC - correction codes
- Source IP Address
- Destination IP Address
- Parameters
- Payload

---

**DSCP**

...

---

**ECN**

...

---

**Fragmentation**

If packet has a huge size, it's divided by several small-size fragments. This process named *fragmentation*. Router compiles packet from the got fragments. Fragmentation process uses three fields:

- Identification - fragments of one packet have the same value. Router uses it to identify belonging to one packet.

- Flags - 3 bits: DF (*Don't Fragment*), MF (*More Fragments*) and reserved bit. *DF* bit forbids to fragment the packet. *MF* bit indicates that current fragment is not last of this packet. Router uses *MF* to identify beginning and ending of packet fragments set.

- Fragment Offset - Router uses it to identify the order of fragments in packet.

  Fragmentation is produced if packet size more then *MTU*. *MTU* (*Maximum Transmission Unit*) - is unit size, transmitted by Ethernet frame (*payload*). *IEEE 802.3* set size of Ethernet frame in 1518 bytes. This chose based on different factors - network tasks, loading, transmitting data, distance etc. 18 bytes used for headers, except the *preambula*. Don't forget about *LLC, SNAP, dot1q, qinq* that can add extra headers. The remaining 1500 bytes used for payload. There are frames with size from 1500 to 16000 bytes - *jumbo frames*. They used in specific tasks.

---

**Parameters**

*Parameters* is optional header, that common used for a debugging information. This header consists of several fields of one of eight predefined types. In these fields, you can specify the exact route, register routers traveled by the packet, place security data or time stamps.

Since the number of fields in the *parameters* header can be arbitrary, several zero bytes must be added at the end of the header to align the packet header with a 32-bit boundary.

---

**IP Addresses**

IPv4 address consists of 32 bits. It's decided to represent the address as 4 octets in decimal notation as a numbers from 0 to 255 divided by dot. IPv4 address consists of two parts: network number and host number. For differences network and host numbers subnet mask used.
Example: 181.3.25.103

Subnet mask is bits mask, that consists of 32 bits, where in the beginning there are 1, followed by 0. Subnet mask represents as well as IPv4 address.
Example: 255.255.0.0

Minimal network consists of 3 address - network address (the first address from range), broadcast address (the last from range), host address. For connectivity with another L3 networks it's availability required of the fourth address - default gateway.

There are two types of addressing:

- Classful Addressing
- CIDR (*Classless Inter-Domain Routing*)

**Classful Addressing**

![classful-addressing](/home/leschev/Projects/network-cheat-sheets/images/protocols-standards-and-mechanisms/network-layer/ip/classful-addressing.png)

By classful addressing all the address space is divided to 5 classes:

- A - used for /8 networks
- B - used for /16 networks
- C - used for /24 networks
- D - used for multicast. Uses /24 subnet mask.
- E - reserved. Also uses /24 subnet mask.

Router distinguishes classes by first bits in the address. A - 0, B - 10, C - 110, D - 1110, E -1111. Router reads first bits until meet 0 or doesn't read four bits. By fact, this classful bits are immutable, so network address uses 32 - X - Y bits, where X is classful bits and Y is host bits.

**CIDR**

...

---

**IPv6**

...

---

