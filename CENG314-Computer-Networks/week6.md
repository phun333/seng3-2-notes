# CENG 314 - Transport Layer: Midterm Study Notes (TCP Congestion Control & QUIC)

## Slide 1: Transport Layer: Overview

*   **Transport Layer:**  This layer is like a delivery service for applications. It makes sure data gets to the right place, reliably or quickly (depending on what the application needs).
*   **Transport services and protocols:**  Different ways to send data (like letters or packages).
*   **Multiplexing and demultiplexing:**  Sharing one delivery truck (IP address) among many applications (like web browser and email).
*   **Connectionless transport (UDP):**  Like sending a postcard – fast, but no guarantee it will arrive.
*   **Connection-oriented transport (TCP):**  Like sending a registered letter – slower, but you know it arrives.
*   **TCP Congestion Control:** How TCP avoids making the internet too busy.
*   **Evolution of transport-layer functionality:**  How transport protocols are getting better (like QUIC).

## Slide 2: TCP Congestion Control

*   **TCP Congestion Control:** Methods that make sure the network doesn't get too busy.
*   **Reliable data transfer:** Fixes data that's lost.
*   **Network congestion:** When the network is too busy and slow.
*   **Throttle senders:** Control how fast computers send data.
*   **Little congestion:** Send faster.
*   **High congestion:** Send slower.
*   How does a TCP sender limit its sending rate?
*   How does a TCP sender perceive a congestion?
*   What algorithm is used to change the sending rate?

## Slide 3: TCP Congestion Control (How to limit sending rate?)

*   **Flow control:** Limiting sender's data flow.
*   **Congestion window (cwnd):** How much data a sender can send at once. It is limited.
*   **Constraint:** Rate at which a TCP sender can send traffic.
*   **Unacknowledged data:** Amount of data not exceeding the minimum of cwnd and rwnd.
*   **cnwd/RTT: sender rate:** Formula used for sending rate.

## Slide 4: TCP Congestion Control (How to perceive congestion?)

*   **Excessive congestion:** Too many computers sending data.
*   **Router buffers overflow:** Route overflow, and then the TCP segment is dropped.
*   **Loss Event at Sender:** Indications of congestion.
*   **ACKs to trigger:** TCP uses ACKs to measure how fast it is being received.

## Slide 5: TCP Congestion Control (Algorithm to change sending rate?)

*   **TCP senders determine their sending rates:** Making use of all available bandwidth.
*   **TCP Sender's rate:** Needs to be decreased during congestion.
*   **Lost segment implies congestion:** Lost data segments suggest congestion.
*   **Sender's rate can be increased:** When ACK arrives.
*   **Bandwidth probing:** Increase transmission to probe for rates where congestion begins.
*   **Start Decreasing the rate:** When loss occurs.

## Slide 6: TCP Congestion Control: Details

*   The TCP algorithms have 3 components:
    *   Slow start
    *   Congestion avoidance
    *   Congestion detection

## Slide 7: TCP Congestion Control: Details

*   **Cwnd:** Starts small.
*   **TCP Sending Behavior:** Send, then wait.
*   **TCP Rate Formula:** TCP = cwnd/RTT
*   **TCP Sender Limits Transmission:** `LastByteSent - LastByteAcked < cwnd`
*   **Adjusted in response:** Adjusted to the network congestion.

## Slide 8: TCP Slow Start

*   **Slow Start:** When a TCP connection starts, the sender sends data slowly at first.
*   **Increase rate exponentially:** As acknowledgements come back, the sender sends faster.
*   **Doubles every RTT:** Doubles how much data it sends until it detects the loss.
*   **Summary:** At first slow, but then fast.

## Slide 9: TCP: From Slow Start to Congestion Avoidance

*   **Exponential increase should switch to linear?:** Finding when to switch.
*   **Variable ssthresh:** Used to switch from the exponential to linear increase.
*   **Each time acknowledgement is received:** Increment the size by 1 (cwnd = cwnd + 1).
*   **Equal to receiver window size:** Continue until equal to window size (free buffer, rwnd).

## Slide 10: Congestion Detection

*   **Decrease size when congestion occurs:** Cwnd needs to decrease for TCP.
*   **Need for retransmission:** Need for understood congestion.
*   **If timeout:** TCP needs to take timeout as one of the factors.
*   **If 3 Duplicate ACKs:** Then TCP uses ACKs.

## Slide 11: Congestion Detection (Timeout)

*   Visualizes congestion detection with Timeout, when slow start phase begins again.

## Slide 12: Congestion Detection (3 Duplicate ACKs)

*   Visualizes congestion detection with 3 Duplicate ACKs, when congestion avoidance phase begins.

## Slide 13: TCP Congestion Control: AIMD

*   **AIMD (Additive Increase Multiplicative Decrease):**  TCP's main way of controlling congestion.
*   **Approach:** Senders can increase, then decrease.
*   **Additive Increase:** Increase sender rate by 1, after waiting a round-trip time (RTT).
*   **Multiplicative Decrease:** Reduce send rate by half after waiting a round-trip time (RTT).
*   **Probing for bandwidth:** AIMD sawtooth behavior.

## Slide 14: TCP CUBIC: Changes the Avoidance Way

*   **Usual way to decrease:** Decrease sending rate, and then increase.
*   **Increase rate quickly:** Ramp up to get close to pre-loss.
*   **After cutting rate/window:** Ramp up and take it slowly.

## Slide 15: Transport Layer: Roadmap

*   Same slide as slide 1.

## Slide 16: QUIC: Quick UDP Internet Connections

*   **QUIC:** A newer way to send data that's faster than TCP.
*   **UDP:** It is built on top of UDP (User Datagram Protocol).
*   **Secure HTTP:** Improves secure HTTP (HTTPS).
*   **Google:** Used by Google.
*   **UDP transport-layer protocol:** UDP protocol is as its underlying transport-layer protocol.
*   **Connection establishment, error control, and congestion control:** The approaches it adopts.

## Slide 17: QUIC: Connection Establishment

*   **Connection Establishment:** The connection needs to be set up beforehand.
*   **TCP Connection + TLS:** Two steps to create the setup.
*   **QUIC: 1 handshake:** Only one step to create the connection.