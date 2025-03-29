# CENG 314 - Network Layer (Week 5) - Study Notes

These notes provide a concise overview of the Network Layer, focusing on key concepts and important terms for midterm preparation.

## Slide 1: The Network Layer

*   Moving data packets from one "host" (computer) to another.
*   Two important jobs:
    *   **Forwarding:**  Moving a packet from an input to the output of the router.
    *   **Routing:**  Figuring out the best path for packets to travel from one host to another.

## Slide 2: Network Layer

*   **Data plane:**  Forwarding datagrams from input links to output links. *Fast* (done in hardware).
*   **Control plane:**  Routing. How the routers determine the path the data will take. *Slower* (done in software).

## Slide 3: Network layer: two key functions

*   **Forwarding:** Data plane
    *  Move packets from the incoming interfaces to the outgoing interfaces
    *  Based on header and the forwarding table

*   **Routing:** Control plane
    *  Determine the route from source to destination

## Slide 4: Control plane: approaches

*   Two ways to control the routing:
    *   **Traditional routing algorithms:** Routing algorithms like the RIP and OSPF routing algorithms
    *   **Software-Defined Networking (SDN):** Control plane is implemented on the external system. The network devices only implement the data layer (forwarding).

## Slide 5: Network service model

*   "Guarantees" a network can provide.
*   Examples:
    *   Reliable delivery (data arrives correctly).
    *   Guaranteed bandwidth (minimum speed).
    *   Limited delay.

## Slide 6: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 7: Network layer: Overview

*   Transport segment to datagram
*   Header contains destination address

## Slide 8: Key concepts

*   **Virtual Circuit Network (VC):** Acts like a phone call. A *path* is set up in advance and all packets follow the same path. Connection established, data transfer, connection teardown
*   **Datagram Network:** Acts like sending letters. Each packet is routed independently.  (A1/A2: self-contained and don’t depend on any previous packet)

## Slide 9: Virtual circuits: signaling protocols

*   Used to setup, maintain teardown VC

## Slide 10: Datagram networks: routing

*   Each router has a "forwarding table" to direct packets
*   Destination address in datagram
*   It looks up address in table and decides output link

## Slide 11: Datagram forwarding table

*   How to forward the datagram to its destination with longest prefix matching.

## Slide 12: Longest prefix matching

*   When looking for the longest prefix matching, you have to select the largest prefix:

## Slide 13: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 14: Inside a router

*   Input port, switching fabric, output port

## Slide 15: Router architecture overview

*   Shows the architecture of the router with input ports, switching fabric, output ports, routing processor.

## Slide 16: Input Port functions

*   **Decentralized switching:**
        *  Given datagram destination, look up output port using forwarding table in input port memory
        *  Goal: complete input port processing at ‘line speed’
        *  Queuing: delay

## Slide 17: Switching Fabrics

*   Move packets from input buffers to output buffers.
*   Three types of switching fabrics:
    *   Memory
    *   Bus
    *   Crossbar

## Slide 18: Switching via memory

*   The packet goes to the routing processor first, then copy to the output interface.
*   Limited by memory bandwidth.

## Slide 19: Switching via a bus

*   Input port gets packet, puts it on the shared bus, output port grabs the packet.

*   **Bus contention:**  Only one packet can use the bus at a time, so it's slow.

## Slide 20: Switching via interconnection network

*   More complex, uses a crossbar.
*   Multiple packets can be transferred in parallel.

## Slide 21: Output Ports

*   **Output port queuing:** Buffering required when arrival rate via switch exceeds output line speed
    *  Queuing (delay) and loss due to output port buffer overflow

## Slide 22: Output queuing (cont.)

*   **Head-of-the-Line (HOL) blocking:** Queuing happens when there are multiple packets waiting in front of the queue but only one can be output at a time because it is occupied.

## Slide 23: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 24: The Internet Protocol (IP):

*   IP: the addressing convention and data format
*   What all internet device has.

## Slide 25: IPv4 addressing

*   32 bit number (4 billion addresses)
*   Addresses are written in dotted decimal notation.
        *  Each number is between 0-255

## Slide 26: IP address: how to get one?

*   How do hosts get IP address?
    *   Hardcoded (host has a file in the computer, e.g. /etc/network/interfaces)
    *   DHCP: Dynamic Host Configuration Protocol

## Slide 27: DHCP: Dynamic Host Configuration Protocol

*   DHCP: dynamically get address from server

## Slide 28: DHCP overview

*   DHCP discover:
         *  Client broadcast "DHCP discover" msg (optional)
*   DHCP server offer:
         * server(s) respond with "DHCP offer" msg (IP
         address, lease time, server IP address)
*   DHCP request:
         *  client requests offered IP address
*   DHCP ack:
         * server sends ACK

## Slide 29: DHCP: example

*   DHCP is a complex message.

## Slide 30: DHCP: more than address allocation

*   DHCP can also provide:
    *   address of first-hop router for client
    *   name and IP address of DNS server
    *   network mask (indicating network versus host portion of address)

## Slide 31: Network address translation (NAT)

*   The ISP only gives you one IP address, but in the back the NAT helps transfer multiple IP addresses to the Internet
*   Allows multiple devices in a home network to share a single public IP address.

## Slide 32: NAT: motivation

*   Local network only uses one IP address
        *  Range of addresses not needed from ISP: just one IP address for all devices
        *  Can change address of devices in local network without notifying provider
        *  Allows changing ISP without changing address devices in local network
        *  Devices inside the local network are not explicitly addressable, visible by outside world

## Slide 33: NAT: translation table

*   The table to translation from address to other destinations

## Slide 34: NAT: example

*   Step by step process to how the data is transferred to destination network

## Slide 35: NAT: controversity

*   The internet should be about one world, without NAT the addresses do not have full connectivity to one another:
        * Routers are not only there for translation it should only there for forwarding and security
*   It violates end-to-end argument
        * NAT must inspect transport layer port number

## Slide 36: IPv6

*   With the growth of Internet-connecting devices, 32-bit IP address space soon fully allocated
*   New IP version 6 (IPv6)
        *  Datagram format:
                *  Expanded addressing capabilities
                *  Header format simplification

## Slide 37: IPv6 datagram format

*   128-bit source, destination IP address
*   Flow label: identify datagrams in same "flow" (concept of "traffic class")
*   Next header: identify upper layer protocol for data

## Slide 38: Transitioning from IPv4 to IPv6

*   Not all routers can be upgraded simultaneously
         * -> how will network operate with "mixed" IPv4 and IPv6 routers?
*   Two Tunneling: IPv6 datagram carried as payload in IPv4 datagram among IPv4 routers

## Slide 39: Tunneling

*   IPv6 datagram is put inside IPv4 datagram for the connection

## Slide 40: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 41: Routing Algorithm goal

*   Graph abstraction for routing algorithms
*   Node abstraction for a graph abstractions
*   Abstraction that can be used to connect many nodes

## Slide 42: Graph abstraction

*   Cost should always be the lowest.
*   lowest values has to be forwarded.

## Slide 43: Classification of routing algorithms

*   *Global*: all routers have complete topology, link cost info
*   *Decentralized*: router knows physically-connected neighbors, link costs to neighbors
*   *Static*: routes change slowly over time
*   *Dynamic*: routes change more quickly
         * Periodic update
         * Direct response to link cost changes

## Slide 44: Routing algorithms: Link state

*   With link state, the node have to have all the information about its connecting states.

## Slide 45: Dijkstra’s algorithm: notation

*   c(x,y): link cost from node x to y; ∞ if not direct neighbors
*   D(v): current value of path cost from source to node v
*   p(v): predecessor node along path from source to v, that is, next to node v
*   N': set of nodes whose least cost path definitively known

## Slide 46: Dijsktra’s algorithm

*   Initialization: S has information to the connection of the source.
*   When the process ends, the distance of the lowest connection is already found

## Slide 47: Dijkstra’s algorithm: example

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 48: Dijkstra’s algorithm: example (2)

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 49: Dijkstra’s algorithm: example (3)

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 50: Dijkstra’s algorithm: example (4)

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 51: Dijkstra’s algorithm: example (5)

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 52: Dijkstra’s algorithm: example (6)

*   Here is a visual step by step process of Dijsktra's algorithm.

## Slide 53: Dijkstra’s algorithm: complexity

*   Complexity in number of nodes: O(n^2)

## Slide 54: Distance Vector algorithm (Bellman-Ford)

*   Works by having each node maintain a "distance vector" with estimates to all other nodes.
*   Each node exchanges these vectors with neighbors.
*   Iteratively improve estimate.

## Slide 55: Bellman-Ford example

*   Shows how the algorithm work by the iteration.

## Slide 56: Distance vector: link cost changes

*   Each node informs neighbors when its DV changes. Neighbors then update their table.
*   This is good but what if some node keeps informing that they are in a minimal connection

## Slide 57: Link cost changes: “count to infinity” problem!

*   Bad news travels slow.

## Slide 58: Distance vector: poisoned reverse

*   If Z routes through Y to get to X:
        * Z tells Y its (Z’s) distance to X is infinite (so Y won’t route to X via Z)
*   Helps prevent some loops

## Slide 59: Comparison of LS and DV algorithms

*   Message complexity
*   Convergence

## Slide 60: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 61: Interplay between routing, forwarding

*   Graph abstraction is useful in the algorithms
*   Forwarding requires low level design and the algorithm does all work

## Slide 62: Hierarchical routing

*   Routers are organized into "autonomous systems" (AS).
*   Routers *within* the same AS use the same routing algorithm.
*   "Gateway routers" connect different ASes.

## Slide 63: Internet AS organization

*   Autonomous systems in the Internet connect to each other

## Slide 64: Internet routing: intra-AS

*   Also known as "interior routing protocol"
*   Examples:
        * RIP: Routing Information Protocol
        * OSPF: Open Shortest Path First
        * IGRP: Interior Gateway Routing Protocol

## Slide 65: RIP (Routing Information Protocol)

*   Distance vector algorithm
*   Distance metric: # of hops (max 15 hops)

## Slide 66: OSPF (Open Shortest Path First)

*   Uses link state algorithm.
*   Each router constructs a complete topological map of entire AS

## Slide 67: Internet routing: BGP

*   **BGP (Border Gateway Protocol):** The routing protocol between ASes.

## Slide 68: BGP basics

*   BGP provides each AS means to:
        * Obtain subnet reachability information from neighboring ASs.
        * Propagate reachability information to all AS-internal routers.
        * Determine “good” routes to other networks based on reachability information and policy.

## Slide 69: eBGP and iBGP

*   iBGP and eBGP helps determine the protocol for BGP and each protocol takes care of something specific.

## Slide 70: BGP path attributes

*   BGP route is determined by : Route by the value of prefix, prefix attributes that contains route.

## Slide 71: BGP route selection

*   Routers select route from the choices

## Slide 72: BGP: why different intra- and inter-AS routing?

*   Intra-AS: policy is not necessarily needed.
*   Inter-AS: policy is extremely important.

## Slide 73: Chapter 4: network layer

*   Here are the chapter 4 roadmap that we are going to explore:
      * Virtual circuit and datagram networks
      * Inside a router
      * Internet protocol: IPv4, addressing, IPv6
      * Routing algorithms
      * Broadcast and multicast routing

## Slide 74: Broadcast routing

*   Deliver the packets for all nodes:
        * Source duplicate approach: makes the source to duplicate all the packets
        * Inefficient

## Slide 75: Broadcast routing: controlled flooding

*   To minimize the broadcast, it checks before forwarding:
        *  Node only broadcast if it hasn't broadcasted before
        *  Node keeps track of packet already broadcast
        *  Source node puts broadcast ID number in packet

## Slide 76: Spanning tree

*   No redundant packets
*   Graph can be drawn without any nodes intercepting with each other

## Slide 77: Multicast routing: a “best possible” tree?

*   Minimizes cost to destination
*   Steiner tree: minimum cost tree connecting all members of the group
• problem is NP-complete

## Slide 78: Approaches for building a multicast routing tree

*   How to build this tree given group members and router connectivity:
    *   source-based tree: one tree for each source and receivers
    *   group-shared tree: group uses one tree no matter who is sending

## Slide 79: Tunneling

*   Multicast datagram with non-multicast capable routers: datagram “tunneled” thru “overlay” network:

That should cover all the slides! Remember to review the specific algorithms and examples in more detail. Good luck on your midterm!