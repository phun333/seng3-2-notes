# CENG 314 - Wireless and Mobile Networks (Week 7) - Study Notes

These notes provide a concise overview of Wireless and Mobile Networks, focusing on key concepts and important terms for midterm preparation.

## Slide 1: Wireless Networks

*   Wireless hosts
        * Laptops, smartphones
        * Run applications.

## Slide 2: Elements of Wireless Networks

*   **Wireless host:** Computer/device that can connect without wires.
*   **Base station:**  Like a wired router, but for wireless connections. (A1/A2: Like a cell phone tower). Connects wireless clients to a wired network.

## Slide 3: Wireless network taxonomy

*   Different types of wireless networks, categorized by range and mobility:
    *   Infrastructure vs. Infrastructure-less.

## Slide 4: Wireless network taxonomy

*   Infrastructure mode
        *  Base station connect wireless devices to the network.
*   Ad hoc mode
         * No base station
         * Nodes can only transmit to other nodes within link coverage
         * Nodes organize themselves into a network

## Slide 5: IEEE 802.11 Wireless LAN

*   Popular wireless LAN technology.
*   Based on IEEE 802.11 standard.
*   Often referred to as "WiFi."

## Slide 6: 802.11 architecture

*   Wireless station with a MAC address
*   Access points is the medium
*   The access point and several wireless is one basic set (BSS).

## Slide 7: 802.11: Channels, Association

*   **Channel:** A range of frequencies used for communication.
*   **Association:** When a wireless device connects to a base station, it's called "association".

## Slide 8: IEEE 802.11: multiple access

*   To avoid the noise, the wireless network uses:
       * CSMA/CA: Sender
          - Has to sense channel and the carrier signal
          - Avoid collision

## Slide 9: IEEE 802.11 MAC protocol: CSMA/CA

*   **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance):** Before sending, a node listens to the channel. If busy, it waits.

## Slide 10: Collision Avoidance: RTS CTS

*   **RTS (Request To Send):** A short control packet is send by the sender first.
*   **CTS (Clear To Send):** After hearing RTS, the receiver node will send CTS.

## Slide 11: 802.11 frame: addressing

*   Four addresses in frame:
         *  Address 1: MAC address of receiving wireless station
         *  Address 2: MAC address of transmitting wireless station
         *  Address 3: MAC address of router interface to which AP is connected
         *  Address 4: used only in ad hoc mode

## Slide 12: 802.11 frame

*   Frame details for better understanding of what protocol is being used and is it secured or not.

## Slide 13: 802.11: mobility, more

*   More protocols that helps mobile units to connect and move between the network.

## Slide 14: Mobility: basics

*   **Home network:** The network to which a mobile device is permanently connected.
*   **Home agent:** Entity within home network performs mobility functions on behalf of mobile

## Slide 15: Mobility

*   Analogy to someone with a permanent address (home network) and a forwarding address at each spot when travelling (visited network).

## Slide 16: Mobility: terminology

*   Permanent address always remains.
*   Foreign agent has care-of-address for mobile.
*   Correspondent: wants to communicate with mobile

## Slide 17: Mobile IP: two approaches

*   Indirect routing:
         * Correspondent addresses packets to mobile’s home address
         * Home agent intercepts packets, forwards to mobile’s care-of-address
*   Direct routing:
        * Correspondent gets foreign address of mobile, sends directly to mobile

## Slide 18: Indirect routing: comments

*   Triangle problem: correspondent-home-network-mobile

## Slide 19: Direct routing

*   Correspondent requests foreign address from home agent
    * Care-of address

## Slide 20: Communicating with a mobile: summary

*   Many details skipped for clarity:
          *  authentication (ensure correspondent is really talking to mobile)
          * registration with HA
          *  multiple foreign agents
*   Keep it simple, stupid: why so complicated?
          *  want to maintain transparency: Hmmm, let me think

## Slide 21: Mobile networks: GSM

*   GSM is the most common mobile network

## Slide 22: Components of GSM network architecture

*   Components in GSM for cellular network and their functionalities.

## Slide 23: GSM: setting a call: Visited network

*   Process of setting a call through the cellular network.

## Slide 24: GSM: handoff with common MSC

*   Handoff is the process of change a connection during conversation.

## Slide 25: Why a new layer: mobile?

*   “First principles” not violated: keep it simple stupid!