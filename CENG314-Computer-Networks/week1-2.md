# CENG 314 - Chapter 1: Introduction - Study Notes

These notes provide a concise overview of Chapter 1, focusing on key concepts and important terms for midterm preparation.

## Slide 1: Introduction - CNs and the Internet

*   **Chapter Goal:** Basic understanding of computer networks and the Internet. Learn key vocabulary.
*   **Overview/Roadmap:**
    *   What *is* the Internet? What is a "protocol" (set of rules)?
    *   **Network Edge:** Devices like computers and phones that connect to the internet (hosts).
    *   **Network Core:** The main part of the network that moves data around (like highways).
    *   **Performance:** How well the network works (speed, delays - loss, throughput).
    *   **Protocol Layers:** Model of how data is sent, each layer provides services to upper layer.
    *   **Security:** Keeping the network safe from attacks.
    *   **History:** Brief overview of the Internet's evolution.

## Slide 2: The Internet

*   The Internet is the main way we'll discuss computer networks and the protocols that run them.
*   Two views of the Internet:
    *   "Nuts and bolts" view: Hardware (physical parts) and software (programs).
    *   "Services" view: A system that provides things for apps to use.

## Slide 3: The Internet

*   The Internet is a network connecting billions of devices globally.
*   Connects computers, TVs, gaming systems, home appliances, etc.
*   Devices ("hosts" or "end systems") connect using links and "packet switches."

## Slide 4: The Internet: a "nuts and bolts" view

*   **Devices:** Billions of connected "hosts" (end systems).
*   **Packet Switches:** Devices that move data ("packets") forward. Routers and switches.
*   **Communication Links:** Connect devices. Fiber optic, copper wire, wireless. "Bandwidth" is the data capacity.
*   **Networks:** Devices, routers, and links managed by an organization.

## Slide 5: Internet-connected devices

*   Examples of common internet-connected devices.

## Slide 6: The Internet: a "nuts and bolts" view

*   **Internet:** "Network of networks."
*   Interconnected ISPs.
*   **Protocols:** Rules for how data is sent/received. Examples: HTTP, TCP, IP, WiFi, 4G.
*   **Internet Standards:** Rules everyone agrees on.
    *   **RFC:** "Request for Comments" - documents describing how things work.
    *   **IETF:** "Internet Engineering Task Force" - makes the standards.

## Slide 7: The Internet: a "services" view

*   The Internet *provides* services to applications (websites, video, email, games).
*   Provides a way for apps to connect and send data via a "programming interface" (socket).
*   Provides different service options to apps.

## Slide 8: What's a protocol?

*   **Protocols** define how messages are sent and received between network entities.
*   **Human protocols:** Initiate communications with specific messages
*   **Network protocols:** Rules for computers (devices).
    *   Govern everything happening on the Internet.
*   Protocols define: Message format, order of messages, and actions taken.

## Slide 9: What's a protocol?

*   A simple analogy of human vs computer networks protocol

## Slide 10: Chapter 1: roadmap

*   Recap of topics covered so far.

## Slide 11: A closer look at Internet structure

*   **Network Edge:**
    *   "Hosts" (end systems): clients and servers.
    *   Servers are often in data centers.

## Slide 12: A closer look at Internet structure

*   **Network Edge:**
    *   Hosts: clients and servers.
    *   Servers often in data centers.
*   **Access Networks:**
    *   Connect end systems to the first router (edge router).  Wired or wireless.

## Slide 13: A closer look at Internet structure

*   **Network Edge:**
    *   Hosts: clients and servers.
    *   Servers often in data centers.
*   **Access Networks:**
    *   Wired or wireless communication links.
*   **Network Core:**
    *   Interconnected routers.
    *   Network of networks.

## Slide 14: Access networks and physical media

*   **How to connect end systems to edge router?**
    *   Residential Access Nets.
    *   Institutional Access Networks (School, Company).
    *   Mobile Access Networks (WiFi, 4G/5G).

## Slide 15: Access networks: cable-based access

*   Cable, DSL, Fiber and Wireless connections for residential or home access
*   Frequency division multiplexing (FDM): using different channels transmitted in different frequency bands when use the same link for different purposes.

## Slide 16: Access networks: cable-based access

*   Cable internet access makes use of existing cable TV infrastructure.
*   "HFC" (hybrid fiber coax): Fiber optic cable runs to a neighborhood, then coaxial cable connects to individual homes.
*   "Asymmetric": Download speeds are faster than upload speeds.
*   Homes share access network to cable headend

## Slide 17: Access networks: digital subscriber line (DSL)

*   Using existing telephone lines for data.
*   "DSLAM" is a device that separates data and voice signals.
*   Different download and upload speeds (asymmetric).

## Slide 18: Access networks: fiber to the home (FTTH)

*   Each home has an optical network terminator (ONT).
*   A splitter combines a number of homes onto a single, shared optical fiber, which connects to an optical line terminator (OLT) in the telco's central office

## Slide 19: Access networks: home networks

*   WiFi wireless access point combined with a router/modem in a single box

## Slide 20: Wireless access networks

*   Shared wireless network connects the end system to the router (access point)
*   Wireless LANs provide wireless access to the Internet (WiFi).
*   Wide-area cellular access networks (4G, 5G) provide a wireless connection over a wider range.

## Slide 21: Access networks: enterprise networks

*   Mix of wired and wireless technologies.
*   Ethernet (wired) and WiFi (wireless)
*   users transmit/receive packets to/from an access point that is connected into the enterprise's network (most likely using wired Ethernet), which in turn is connected to the wired Internet

## Slide 22: Access networks: data center networks

*   High-bandwidth links connect servers.

## Slide 23: Links: physical media

*   **Bit:** The smallest unit of data.
*   **Physical Link:** What connects devices (like a cable).
*   **Guided Media:** Signals travel in a solid medium (copper wire, fiber optic cable).
*   **Unguided Media:** Signals travel freely (radio waves).
*   **Twisted Pair (TP):** Two insulated copper wires
    *   Category 5: 100 Mbps, 1 Gbps Ethernet
    *   Category 6: 10 Gbps Ethernet

## Slide 24: Links: physical media

*   **Coaxial cable:** two concentric copper conductors, bidirectional broadband
*   **Fiber Optic cable:**:
    *   glass fiber carrying light pulses
    *   high-speed operation.
    *   low error rate.
    *   immune to electromagnetic noise

## Slide 25: Links: physical media

*   **Wireless radio** carries radio bands in electromagnetic spectrum.
*   **Radio link types:**
    *   Wireless LAN (WiFi): 10-100's Mbps.
    *   Wide-area (4G cellular): 10's Mbps over ~10 Km
    *   Bluetooth: cable replacement.
    *   Terrestrial microwave: point-to-point; 45 Mbps channels
    *   Satellite: up to 45 Mbps per channel, high end-to-end delay

## Slide 26: Chapter 1: roadmap

*   Recap of what has been covered.

## Slide 27: The network core

*   The "core" of the network is made of interconnected routers.
*   **Packet switching:**  Data is broken into "packets." Hosts break messages into these packets.
*   Packets are sent from source to destination.
*   Network forwards packets from one router to another

## Slide 28: Two key network-core functions

*   **Forwarding (Switching):** *Local* decision of how to move a packet based on destination
*   **Routing:** *Global* decision that determines the source-destination paths and creates the forwarding tables.

## Slide 29: Packet-switching: store-and-forward

*   Routers receive the *entire* packet before forwarding. This is store and forward
*   **Packet transmission delay:**  the time it takes to transmit an entire packet.

## Slide 30: Packet-switching: queueing

*   Packets can be queued while waiting for the output link transmission.

## Slide 31: Packet-switching: queueing

*   If the buffer fills up with waiting packets, the packets will be dropped

## Slide 32: Alternative to packet switching: circuit switching

*   End-to-end resources are dedicated and reserved between source and destination.
*   Commonly used in traditional telephone networks

## Slide 33: Circuit switching: FDM and TDM

*   **Frequency Division Multiplexing (FDM):** Frequencies divided into narrow frequency bands (narrow).
*   **Time Division Multiplexing (TDM):** time divided into slots. Each call has the full wider band but only at specific times.

## Slide 34: Packet switching versus circuit switching

*   Packet switching allocates link use on demand
*   Packet switching offers better sharing of transmission capacity and is simpler than circuit switching.

## Slide 35: Internet structure: a "network of networks"

*   End systems connect to the internet with ISPs. These ISPs must be interconnected
*   The network is driven by economics and national policies

## Slide 36: Internet structure: a "network of networks"

*   Multiple Tier and Regional ISPs interconnected
*   **Internet Exchange Points (IXP)** are physical locations where Internet infrastructure companies connect with each other
*   Content Provider Networks (CPNs) are private networks that connects its data centers to Internet

## Slide 37: Chapter 1: roadmap

*   Recap of what has been covered.

## Slide 38: How do packet delay and loss occur?

*   **Queueing:** waiting for turn of transmission
*   **Packet loss** when the memory is filled up with packets

## Slide 39: Packet delay: four sources/types

*   **Nodal Processing Delay (d\_proc):** Checking for errors and determining the output link.
*   **Queueing Delay (d\_queue):** Time waiting in the queue at the router.
*   **Transmission Delay (d\_trans):** Time to push the packet onto the link.
*   **Propagation Delay (d\_prop):** Time for the signal to travel across the link.

## Slide 40: Packet delay: four sources

*   Packets are transmitted in a first-come-first-served manner
*   Transmission Delay (d\_trans): L/R
*   Propagation Delay (d\_prop): depends on the length of the link

## Slide 41: Packet queueing delay (revisited)

*   avg queueing delay small when traffic intensity is low
*   the opposite happens when the traffic is high
*   Design your system so that the traffic intensity is no greater than 1

## Slide 42: "Real" Internet delays and routes

*   **Traceroute:** A program that measures the delay from your computer to other routers along the path to a destination.

## Slide 43: Real Internet delays and routes

*   Example of a traceroute program used to track delay

## Slide 44: Throughput

*   **Throughput:** The rate at which data is *actually* sent from sender to receiver.
    *   **Instantaneous:** The rate at a specific moment.
    *   **Average:** The rate over a longer period.

## Slide 45: Throughput

*   The lowest throughput is the bottleneck link

## Slide 46: Throughput: network scenario

*   The bottleneck is often the connection link

## Slide 47: Chapter 1: roadmap

*   Recap of what has been covered.

## Slide 48: Network security

*   The Internet was not built with a lot of security.
*   We now need to protect computer networks: learn how bad guys attack, how to defend, and how to design secure systems.

## Slide 49: Bad guys: packet interception

*   **Packet Sniffing:** Secretly recording copies of data packets that pass by.

## Slide 50: Bad guys: fake identity

*   **IP Spoofing:** Sending packets with a fake "source" address to hide who you are.

## Slide 51: Bad guys: denial of service

*   **Denial of Service (DoS):** Overloading a server with so much traffic that real users can't access it.

## Slide 52: Lines of defense:

*   **Authentication:** Proving you are who you claim to be.
*   **Confidentiality:** Keeping data secret using encryption.
*   **Integrity Checks:** Making sure data hasn't been changed.
*   **Access Restrictions:** Using passwords and VPNs to control who can access a network.
*   **Firewalls:** Specialized devices that block unwanted traffic.

## Slide 53: Chapter 1: roadmap

*   Recap of what has been covered.

## Slide 54: Protocol "layers" and reference models

*   Networks are very complicated.
*   "Layers" help us organize and talk about them.

## Slide 55: Why layering?

*   Layering makes it easier to design, discuss, and update complex systems.
*   Each layer implements a number of protocols

## Slide 56: Layered Internet protocol stack

*   5-layer model:
    *   **Application:** Supports apps (HTTP, DNS).
    *   **Transport:** Sends data between processes (TCP, UDP).
    *   **Network:** Routes data (IP).
    *   **Link:** Sends data between neighbors (Ethernet, WiFi).
    *   **Physical:** Actual bits "on the wire."

## Slide 57: Services, Layering and Encapsulation

*   The Application layer exchanges messages
*   The Transport Layer transfers messages from process to process

## Slide 58: Services, Layering and Encapsulation

*   The Network Layer transfers transport-layer segment

## Slide 59: Services, Layering and Encapsulation

*   The Link Layer protocol transfers datagram

## Slide 60: Services, Layering and Encapsulation

*   Recap of services layering and encapsulation

## Slide 61: Encapsulation: an end-end view

*   Application, transport, network, and physical layering

## Slide 62: Chapter 1: roadmap

*   Recap of what has been covered.

## Slide 63: Internet history

*   1961-1972: Early packet-switching principles
*   1972-1980: Internetworking, new and proprietary networks
*   1980-1990: new protocols, a proliferation of networks
*   1990, 2000s: commercialization, the Web, new applications
*   2005-present: scale, SDN, mobility, cloud

## Slide 64: ISO/OSI reference model

*   The OSI reference model is a seven-layer reference model with two more layers not found in the internet protocol stack!
*   **Presentation:** Allows apps to interpret meaning of data.
*   **Session:** Synchronization and recovery of data.