# CENG 314 - Link Layer (Week 6) - Study Notes

These notes provide a concise overview of the Link Layer, focusing on key concepts and important terms for midterm preparation.

## Slide 1: Link Layer: Introduction, services

*   **Link Layer:**
    *  Transfers datagram from one node to physically adjacent node over a link
*   Used to transmit between two neighboring nodes

## Slide 2: Link layer: context

*   Terminology
        *  hosts and routers = nodes
        *  communication channels that connect adjacent nodes along communication path = links
        *  layer-2 packets = frames

## Slide 3: Link layer services

*   **Framing:** Encapsulating data into a frame

*   **Link access:** Medium Access Control (MAC) "rules" for sharing a link. (A1/A2: Rules to prevent people from talking at the same time)
*   **Reliable delivery:** Guarantees to move data.
*   **Error detection:** Detect if there are errors with the data that has been transferred.

## Slide 4: Link Layer “where”

*   The place at where the link layers are implemented.
    * Each host and router has link layer

## Slide 5: Two Types of “links”

*  **Point-to-point:**
      *  One sender, one receiver
      *  Examples: Dial-Up, ISDN, xDSL
*  **Broadcast:**
      *  Multiple sending and receiving nodes connected to same, single shared channel
      *  Examples: Ethernet, WiFi

## Slide 6: Adapter Communicating

*   Sending side:
        * Encapsulates datagram in frame
        * Adds error checking bits, rdt, flow control, etc.
*   Receiving side:
        * Looks for errors, rdt, flow control, etc
        * Extract datagram, passes to upper layer at receiving side

## Slide 7: Error Detection

*  **Error Detection:** Check to see whether the data has been changed or altered.
*  One of the most important job of the link layers.
*  Not 100% reliable.

## Slide 8: Error Detection and Correction

*   **EDC = Error Detection and Correction bits (redundancy):** bits added by sender for error detection and correction

## Slide 9: Error detection: parity checking

*   Use "parity bits" to check if there are errors.

*   **Single parity checking:**
       * detect single bit errors
*   **Two dimensional parity check:**
       * detect and correct single bit errors

## Slide 10: Parity checking

*   **Single Bit Parity:** Count the number of 1 bits in your packets and add a bit if it is odd number. This bit will say that the count is even bit.

## Slide 11: Two-dimensional parity check

*   Add up the row bits and column bits, then add the parity bits to see if there is any error.
*   Detect and also correct.
*   Error in two dimensions results in a correctable.

## Slide 12: Internet checksum

*   Adding up all of the bytes.
*   Used in UDP protocol
*   Details of the method on how it is calculated is at the previous slides.

## Slide 13: Cyclic Redundancy Check

*   Treat data as a single binary number
*   Divide data by a generator number G: d bits
*   Get remainder R
*   Transfer: data bits + remainder R

## Slide 14: CRC example

*   Examples of how to implement the process from slide 13.

## Slide 15: Link Layer Addressing

*   MAC address
*   LAN address
*   Physical address

## Slide 16: MAC Addresses

*   6 byte (48 bit) address
*   Burned in the adapter ROM, also software changeable

## Slide 17: LAN Addresses (more)

*   MAC addr allocation administered by IEEE
*   Organizationally Unique Identifier (OUI)
        *  First three bytes of address
*   Manufacturer buys portion of MAC address space (to assure uniqueness)
*   Analogy
        *  MAC address: like social security number

## Slide 18: ARP: Address Resolution Protocol

*   **Address Resolution Protocol (ARP):**  Used to translate from IP addresses to MAC addresses.
*   ARP Table has:
       * The MAC address and the IP address

## Slide 19: ARP protocol

*   Each IP address has an ARP table with its MAC address.
*   When there is an ARP in the same network it will return the unicast.
*   ARP will send out a message using IP and the router in its network.

## Slide 20: Addressing: routing to another LAN

*   Walk-through: sending a datagram from one LAN to another
         *  M and S use ARP to find router interface MAC address
         *  M creates frame, sends frame to router
         *  router receives frame, extracts datagram, forwards datagram to S

## Slide 21: Ethernet

*   "Dominant" LAN technology.

## Slide 22: Ethernet frame structure

*   **Preamble:** Synchronizing sender and receiver clocks
*   **Addresses:** destination and source MAC addresses
*   **Type:** Type of the upper layer protocol
*   **CRC:** Error detection.

## Slide 23: Ethernet Technologies: 10BaseT

*   Several different types with increasing bandwidth.

## Slide 24: Multiple Access Links and Protocols

*   Two types of "links":
         * Point-to-point
        * Broadcast (shared wire or medium; wire, cable; wireless)
*   Multiple access problem: how to coordinate access to shared broadcast channel?
        * Single active node A: A transmits at rate of R bps
        * K active nodes: each active node transmits at rate R/K bps ?
                 * Desirable, but doesn’t happen in practice!
        * Coordination is the key for high throughput!

## Slide 25: Multiple Access Protocols

*   Three protocols
        *  Channel Partitioning
        *  Random Access
        *  Taking-Turns

## Slide 26: MAC protocols: a taxonomy

*   A graph that describe if we can access without coordination or not.

## Slide 27: Channel Partitioning MAC protocols: TDMA

*   **TDMA (Time Division Multiple Access):**

*   Each station gets fixed length time slots (length = packet transmission time) in each round
*   Unused slots go idle
*   Example: six-station LAN, 1,3,4 have packet, slots 2,5,6 idle
*   "Wasteful" if nodes are not active all the time.

## Slide 28: Channel Partitioning MAC protocols: FDMA

*   FDMA (Frequency Division Multiple Access)
        * Channel spectrum divided into frequency bands
        * Each station assigned fixed frequency band
*   Unused transmission time slots in frequency bands go idle
*   Example: six-station LAN, 1,3,4 have packet, frequency bands 2,5,6 idle
*   "Wasteful" when it is not active all the time.

## Slide 29: Random Access Protocols

*   Channel not divided, allow "collisions"
*   When collision occurs then the process can retry
*   ALOHA and CSMA

## Slide 30: Pure (unslotted) Aloha

*   Simple, no synchronization
*   When frame arrives, transmits immediately
*   If another frame transmits at same time -> collision
*   Sender detects collision
*   Sender retransmits frame after random delay

## Slide 31: Aloha efficiency

*   Aloha has probability issues so the chance of transmission is very low.
*   Vulnerable time (2 * T_r) = 18%.

## Slide 32: Slotted Aloha

*   Time is divided into "slots"
*   Nodes starts transmitting at the beginning of the slot
*   Nodes are synchronized
*   If two or more nodes transmits into that slot then the node has to retransmit
*   Reduces vulnerable time
*   Vulnerable time still exists! (Single slot).

## Slide 33: Slotted ALOHA pros & cons

*   Pros:
     * single active node can continuously transmit at full rate of channel
     * highly decentralized: only slots in nodes need to be synchronized
     * simple
*   Cons:
       * collisions, wasting slots
       * idle slots
       * nodes may be able to detect collision in less than time to transmit packet

## Slide 34: CSMA (Carrier Sense Multiple Access)

*   Carrier sense: listen before transmit:
    * If channel sensed idle: transmit entire frame
    * If channel sensed busy, defer transmission

## Slide 35: CSMA collisions

*   Collisions can still occur: propagation delay means two nodes may not hear each other’s transmission

## Slide 36: CSMA/CD (Collision Detection)

*   CSMA with collision detection
*   **Collision detection:** Node stops transmitting if it senses that another node is transmitting

## Slide 37: CSMA/CD collision detection

*   Easy in wired LANs: measure signal strengths, compare transmitted and received signals
*   Difficult in wireless LANs: received signal strength overwhelmed by local transmission strength

## Slide 38: CSMA/CD: “what does sender do?”

*   If channel sensed idle, transmit entire frame
*   If channel sensed busy, defer transmission
*   If collision detected, abort transmission:
       * Reduce channel wastage
*   Persist mode
        *  Retry after random delay

## Slide 39: CSMA/CD efficiency

*   T_prop is the maximum propagation delay
*   T_trans is the time to transmit the packet.

## Slide 40: “Taking Turns” MAC protocols

*   Channel partitioning MAC protocols
        *  Share channel efficiently and fairly at high load
               Inefficient at low load: delay in channel access, 1/N bandwidth if only 1 active node!
*   Random access MAC protocols
        *  Efficient at low load: single node can fully utilize channel

## Slide 41: Taking Turns

*   Polling: Master node, can take time because it takes time to poll one by one
*   Token Passing: pass tokens from nodes. It can have single point of failure because of the nodes.

## Slide 42: Hubs vs. Switches

*   **Hubs**: Layer 1 devices (physical layer)
       * Multiple ports
*   **Switches**: Layer 2 devices (link layer)
       * Connect LAN segments with MAC address

## Slide 43: Link Layer: summary

*   The most important thing for this slide is that the link layer helps transfer datagrams from the node to another.

## Slide 44: The slides by author

*   Information about the author.