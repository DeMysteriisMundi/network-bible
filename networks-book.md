# Networks Book

Author: [Nickolay Leschev](https://github.com/DeMysteriisMundi)
Year: 2020

---

## General

### Organizations

**ISO** - International Organization for Standardization. 

**IEEE** *(англ. Institute of Electrical and Electronics Engineers)* - is a professional association for electronic engineering and electrical engineering. Its objectives are the educational and technical advancement of electrical and electronic engineering, telecommunications, computer engineering and allied disciplines.
More: https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers

### Standards

**IEEE 802** - is a family of IEEE standards dealing with local area networks and metropolitan area networks. The services and protocols specified in IEEE 802 map to the lower two layers (Data Link and Physical) of the seven-layer OSI networking reference model. In fact, IEEE 802 splits the OSI Data Link Layer into two sub-layers named logical link control (LLC) and media access control (MAC).
More: https://en.wikipedia.org/wiki/IEEE_802

### Models

#### OSI

**OSI** - just a standard model.

![osi](/home/leschev/Projects/networks-book/images/models/osi.png)

#### TCP/IP

**TCP/IP** - practical model.

![tcp-ip](/home/leschev/Projects/networks-book/images/models/tcp-ip.jpg)

### Topologies

**Physical Topologies** - how nodes are physically placed and connected.

**Logical Topologies** - how data is goes in the physical topology.

#### Bus Topology

![bus-topology](/home/leschev/Projects/networks-book/images/topologies/bus-topology.jpg)

**+**:

- quick and simple to build

**-**:

- at break the whole network will fall

#### Ring Topology

![ring-topology](/home/leschev/Projects/networks-book/images/topologies/ring-topology.jpg)

**+**:

- quick and simple to build
- more stable and reliable than *Bus Topology*
- possible to make reservation with second ring

**-**:

- at break the whole network will fall

#### Star Topology

![star-topology](/home/leschev/Projects/networks-book/images/topologies/star-topology.jpg)



**+**:

- all nodes are connected to the one central node, that works as a repeater 
- more stable and reliable than *Bus Topology* and *Ring Topology*
- at break the only one node will fall

**-**:

- at break with the central node the whole network will fall

#### Full-Mesh Topology

![full-mesh-topology](/home/leschev/Projects/networks-book/images/topologies/full-mesh-topology.jpg)

**+**:

- the most reliable

**-**:

- the most expensive
- the hardest to build the big topology
- the hardest to maintenance the big topology

#### Partial-Mesh Topology

![partial-mesh-topology](/home/leschev/Projects/networks-book/images/topologies/partial-mesh-topology.jpg)

**+**:

- lightweight version of *Full-Mesh Topology*

**-**:

- expensive
- hard to build the big topology
- hard to maintenance the big topology

#### Hybrid Topology

![hybrid-topology](/home/leschev/Projects/networks-book/images/topologies/hybrid-topology.jpg)

**+/-**:

- is a mix of previous topologies with their advantages and disadvantages
- beautiful



