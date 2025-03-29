# CENG 314 - Midterm Study Guide: Network Layer

## Slide 1: Network Layer Overview

*   **Network Layer:** The most complicated layer in the Internet model.
*   **Host-to-host communication:**  Like talking from one computer to another computer. (Like the post office delivers mail from one home to another)
*   **Data and Control Planes:**
    *   **Data plane:** How a router sends data packets. *Intra* = Inside, means the *per router* functions.
    *   **Control plane:** The logic behind *network wide* logic.

## Slide 2: "Data Plane" Roadmap

*   **Network Layer Overview:** Includes Data and Control Plane.
*   **What's inside a router:** Includes input ports, output ports, how the ports switch between each other, and scheduling (like scheduling CPU time for each process)
*   **IP: The Internet Protocol:**  How data is formatted (datagram format), how computers are found on the network (addressing), IPv6.
*   **Generalized Forwarding/SDN:** Using match+action to forward packets using Software Defined Networking
*   **Middleboxes:**

## Slide 3: Network Layer Services and Protocols

*   **Sender (H1) to Receiver (H2):** One computer is sending data to another computer.
*   **NL of H1:** Adds info so it is sent to the next computer
*   **NL of H2:** Delivers it to the right part of the computer
*   **Network Layer Protocols:** are rules that each computer must follow in order to talk to each other.
*   **Routers:**
    *   Looks at the datagrams to send them correctly.
    *   **Data Plane Role:**  Sends data from input to output.
    *   **Control Plane Role:**  Helps data travel the right path.

## Slide 4: Two Key Network Layer Functions

*   **Forwarding (Data Plane):**  Moving packets from a router's input to the right output. Analogy : Get through single interchange.
*   **Routing (Control Plane):**  Figuring out the best path for packets to travel. Analogy : Plan trip from A to B.

## Slide 5: Data Plane, Control Plane

*   **Data Plane:**
    *   *Local* function that forwards to the correct output port.
*   **Control Plane:**
    *   *Network-wide* logic on the route of the datagram from source to destination.
*   **Control-Plane Approaches:**
    *   **Traditional routing algorithms:** implemented in routers.
    *   **Software-defined networking (SDN):** implemented in (remote) servers

## Slide 6: Per-Router Control Plane

*   Each router shares route information with its neighbours, all routers know how to forward packets.

## Slide 7: Software-Defined Networking (SDN) Control Plane

*   SDN: Remote computer tells the router how to forward the traffic. Router performs forwarding according to pre-defined table only.

## Slide 8: Network Service Model

*   **Possible Services:** The network layer can provide different types of delivery:
    *   **Individual datagrams:**
        *   Guaranteed delivery.
        *   Guaranteed delivery within a certain delay.
    *   **Flow of Datagrams**
        *   Delivering datagrams in order
        *   Guaranteed bandwidth to the receiver.
        *   Security

## Slide 9: Network Service Model

*   **Best Effort:** The Internet does NOT guarantee anything (no bandwidth, loss, etc.).

## Slide 10: "Data Plane" Roadmap

*   See Slide 2.

## Slide 11: Router Architecture Overview

*   **Router:** Four components
    *   **Input Ports:** Get data in.
    *   **Output Ports:** Get data out.
    *   **Routing Processor:** (Software) Figuring out *where* packets need to go. Control plane operates in millisecond timescale.
    *   **Switching Fabric:** (Hardware) Physically move packets in router. Data plane operates in nanosecond timescale.

## Slide 12: Input Port Functions

*   Physical Layer Termination: Ending a wire at the router.
*   Link Layer Function: Need this so we can be compatible with the Link Layer
*   **Decentralized Switching:** Lookup in table and decide *where* the datagram should be forwarded to.
*   Input port queuing: Datagrams are arriving at a rate faster than they can be forwarded.

## Slide 13: Input Port Functions

*   **Destination-Based Forwarding:** Forwarding decisions based on the final address, no matter who sent the message.
*   **Generalized forwarding:** Forwarding decisions based on header field values.

## Slide 14: Longest Prefix Matching

*   **Longest Prefix Match:** Use the *longest* matching address prefix to forward the address.

## Slide 15: Longest Prefix Matching

*   Example of how longest prefix matching works

## Slide 16: Longest Prefix Matching

*   Example of how longest prefix matching works

## Slide 17: Longest Prefix Matching

*   If multiple prefixes match a given destination address, use the longest one.

## Slide 18: Switching Fabrics

*   **Switching Fabric:** Transfers packet from input link to the correct output link.
*   **Switching Rate:** N * input rate.

## Slide 19: Switching Fabrics

*   **Switching via Memory**
*   **Switching via Bus**
*   **Switching via interconnection network**

## Slide 20: Switching via Memory

*   Early generation routers signal the routing processor. Then it sends the datagram to the destination.

## Slide 21: Switching via Bus

*   Send to output without the routing processor.
*   **Bus contention:** the speed will be limited by bus bandwidth.

## Slide 22: Switching via Interconnection Network

*   Use a network of horizontal and vertical buses to switch between ports.

## Slide 23: Input Port Queuing

*   If switch slower than input ports combined, will have queueing at input queues.
*   **Head-of-the-Line (HOL) Blocking:**  A datagram at the front of the queue prevents other datagrams from moving forward.

## Slide 24: Output Port Queuing

*   **Buffering:** Datagrams arrive faster than they can be sent, so we have to store them.
*   **Drop policy:** Choosing which datagrams to drop to free space.

## Slide 25: Output Port Queuing

*   Buffering when arrival rate exceeds line speed.

## Slide 26: Packet Scheduling: FCFS

*   **FCFS (First-Come, First-Served):** Datagrams are sent in the order they arrived.

## Slide 27: Scheduling Policies: Priority

*   **Priority Scheduling:** Send more important datagrams first, and can classify header fields

## Slide 28: Scheduling Policies: Round Robin

*   Each class of queue has an equal opportunity and is served in a round robin (cyclically).

## Slide 29: Scheduling Policies: Weighted Fair Queueing

*   **Weighted Fair Queueing (WFQ):** Like round robin but certain queues get more time.

## Slide 30: Router Architecture Summary

*   Input ports, output ports, a routing processor, and switching fabric.
*   **In traditional routers**, routers execute the routing protocols.
*   **In SDN routers**, a remote computer is responsible for communicating with the routers.

## Slide 31: "Data Plane" Roadmap

*   See Slide 2.

## Slide 32: Network Layer: Internet

*   Network layer functions of a host/router

## Slide 33: IP Datagram Format

*   Shows all the fields of an IP Datagram.
*   IPv4 has a header size of 20 bytes.

## Slide 34: IP Addressing: Introduction

*   **IP Address:** A number that identifies computers in the internet.
*   **Interface:** Connection between computer and physical link.

## Slide 35: IP Addressing: Introduction

*   IP addresses are classful, as in IPv4
*   Classes are A,B,C,D, and E.

## Slide 36: IP Addressing: Introduction

*   Show ranges of classes for IP address.

## Slide 37: IP Addressing: Introduction

*   Reserved Address ranges

## Slide 38: IP Addressing: Introduction

*   The first byte is between 128 and 191. Hence Class B
*   The block has a netid of 132.21.
*   The addresses range from 132.21.0.0 to 132.21.255.255

## Slide 39: IP Addressing: Introduction

*   A mask is a 32-bit binary number
*   The mask is ANDed with IP address to get the block address (network address)
*   Class A default mask is 255.0.0.0
*   Class B default mask is 255.255.0.0
*   Class C Default mask 255.255.255.0

## Slide 40: Subnets

*   **Subnet:** A part of a network where devices can directly reach each other.
*   IP addresses have structure, meaning the first bits are used for knowing what subnet it is, and the remaining bits indicate which computer is part of the network.

## Slide 41: Subnets

*   Show how Subnets improve netword performance.

## Slide 42: Subnets

*   Default Mask
*   Subnet Mask

## Slide 43: Subnets

*   Subnets are networks in a big network!

## Slide 44: Subnets

*   Different ways of visualizing subnetworks.

## Slide 45: IP Addressing: CIDR

*   **CIDR (Classless Inter-Domain Routing):**
    *   Instead of fixed network sizes (like Class A, B, C), CIDR lets you pick how big your network is!
    *   `a.b.c.d/x` means that the first *x* bits define the subnet.

## Slide 46: IP Addresses: How to Get One?

*   **Two Questions:**
    1.  How does a computer get an IP address in its *own* network?
    2.  How does a *network* get its IP address to begin with?
*   **How does a computer (host) get IP address?**
    *   **DHCP (Dynamic Host Configuration Protocol):**  A server gives it an address.

## Slide 47: DHCP: Dynamic Host Configuration Protocol

*   Goal: the client needs to retrieve an IP to join network
*   Can renew address.
*   Reuse addresses
*   DHCP:
    *   DHCP Discover
    *   DHCP Offer
    *   DHCP Request
    *   DHCP Ack

## Slide 48: DHCP Client-Server Scenario

*   Typically, DHCP server will be co-located in router, serving all subnets to which router is attached.

## Slide 49: DHCP Client-Server Scenario

*   Shows the steps of how clients and servers communicate during DHCP.

## Slide 50: DHCP: More than IP Addresses

*   First-hop router address
*   DNS sever
*   Network Mask

## Slide 51: IP Addresses: How to Get One?

*   ISPs (Internet Service Provider) get IPs from the Internet Corporation for Assigned Names and Numbers (ICANN).

## Slide 52: Hierarchical Addressing: Route Aggregation

*   Hierarchical addressing improves efficiency of routes.

## Slide 53: IP Addressing: Last Words

*   **ICANN:** Who manages and hands out IP addresses
*   **NAT** is to help IP exhaustion
*   **IPv6** will also help since it supports way more IPs

## Slide 54: NAT: Network Address Translation

*   **NAT:** Allows all computers in a home network to share a single public IP address.

## Slide 55: NAT: Network Address Translation

*   Benefits of NAT

## Slide 56: NAT: Network Address Translation

*   Explains how NAT works step by step.

## Slide 57: NAT: Network Address Translation

*   Diagram on how NAT works.

## Slide 58: IPv6: Motivation

*   **Motivation:** IPv4 has address space exhaustion, and IPv6 is better

## Slide 59: IPv6 Datagram Format

*   Fixed header of 40 bytes, source/dest address of 128 bits, flow label for classifying flows.

## Slide 60: "Data Plane" Roadmap

*   See Slide 2.

## Slide 61: Generalized Forwarding: Match Plus Action

*   match bits of packet and perform action based on that using forwarding table.

## Slide 62: Flow Table Abstraction

*   Flow Table
*   Match
*   Action

## Slide 63: Flow Table Abstraction

*   See how to match packets and perform actions accordingly in this slide.

## Slide 64: OpenFlow

*   Shows many items that can be matched with OpenFlow, such as ingress ports, MAC address, IP addresses, and so on.

## Slide 65: OpenFlow: Examples

*   Shows common examples of OpenFlow, such as destination-based forwarding and firewalls.

## Slide 66: OpenFlow: Examples

*   Shows common examples of OpenFlow, such as layer 2 destination-based forwarding.

## Slide 67: OpenFlow Abstraction

*   Router: Forward
*   Switch: Forward or Flood
*   Firewall: Permit or Deny
*   NAT: Rewrite address

## Slide 68: OpenFlow Example

*   Describes how OpenFlow orchestrates how traffic flows across a network.

## Slide 69: OpenFlow Example

*   Describes how OpenFlow orchestrates how traffic flows across a network.

## Slide 70: "Data Plane" Roadmap

*   See Slide 2.

## Slide 71: Middleboxes

*   "Middlebox" is anything on the path that performs operations other than forwarding.

## Slide 72: Middleboxes Everywhere

*   NAT, firewalls, IDS, load balancers, and caches are all examples of middleboxes.