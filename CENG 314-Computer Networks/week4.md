# CENG 314 - Transport Layer (Week 4) - Study Notes

These notes provide a concise overview of the Transport Layer, focusing on key concepts and important terms for midterm preparation.

## Slide 1: Transport Layer

*   **Logical communication:** Apps think they're directly connected, even if far apart.
*   Transport layer *protocols* give this illusion.
*   Transport vs network layer:
        *  Network layer : moves packets from a host to another.
        *  Transport layer : delivers packets from process to process.

## Slide 2: Transport layer protocols

*   Two main protocols in the transport layer:
    *   **TCP (Transmission Control Protocol):**  Reliable, connection-oriented. (A1/A2: like a guaranteed delivery service)
    *   **UDP (User Datagram Protocol):**  Unreliable, connectionless. (A1/A2: like sending a postcard - no guarantee)
    *   All hosts in the transport layer has at least one.

## Slide 3: Transport layer vs. network layer

*   Analogy with a 12-person analogy.
*   Transport layer: what the driver provides
        * getting all the boxes to the right people
*   Network layer:
        *  what the truck system provides
        *  getting boxes from a building to another.

## Slide 4: Multiplexing and demultiplexing

*   **Multiplexing (at the sender):** Taking data from different applications and adding "headers" to pass to network layer. (A1/A2: Like collecting mail from different people and putting them in one bag).
*   **Demultiplexing (at the receiver):** Using header information to send data to correct application. (A1/A2: Like sorting mail based on the address.)

## Slide 5: Demultiplexing

*   Host receives IP datagrams
    *   each datagram has source IP address, destination IP address
    *   each datagram carries one transport-layer segment
    *   each segment has source, destination port number
*   host uses IP address & port number to direct segment to appropriate socket
*   (IP addr, port number)
        *  completely specify receiving host receiving socket

## Slide 6: Demultiplexing: connectionless

*   Connectionless demultiplexing means UDP.
*   Create socket = using (IP addr, UDP port #)

## Slide 7: Connectionless demux: example

*   Shows how client X and client Y with different ports sends data to a Server Z with a specific port 6428.

## Slide 8: Demultiplexing: connection-oriented

*   Connection-oriented means TCP.
*   TCP socket identified by 4-tuple:
        * source IP address
        * source port number
        * dest IP address
        * dest port number

*   Demux: receiver uses all four values to direct segment to appropriate socket

*   Server may support many simultaneous TCP connections;
        * Web server each connected client gets dedicated TCP connection

## Slide 9: Connection-oriented demux: example

*   Shows how TCP works but also how all information is need for each TCP's 4-tuple information.

## Slide 10: TCP: reliable data transfer

*   How to send reliable data transfer (rdt) over an unreliable link.
*   Important terms:
    *   **rdt_send():** sending data
    *   **deliver_data():** deliver data to the upper layer
    *   **udt_send():** send packets over the unreliable layer
    *   **rdt_rcv():** receive data.

## Slide 11: Reliable data transfer (rdt): roadmap

*   rtd 1.0 is what it means to send reliable transport over a reliable channel.
*   rtf 2.0, rdt 2.1, rdt 2.2 is what it means to send reliable transport over a channel with bit errors.
*   rdt 3.0 is what it means to send reliable transport over a channel with errors and loss packets.

## Slide 12: rdt 1.0: reliable transfer over a reliable channel

*   The sender sends the packets and the receiver extract them
*   "reliable channel" means nothing can go wrong (no bit errors, no loss)
*   Simplest case, just send and receive.

## Slide 13: rdt 2.0: channel with bit errors

*   Sender sends data and waits for a response.
*   Receiver tells the sender if received package is OK (ACK) or not OK (NAK).
*   If NAK, sender resends.
*   It is very efficient but what if the ACK or NAK got corrupted?

## Slide 14: rdt 2.1: sender, handles garbled ACK/NAKs

*   Sender adds a sequence number to each packet.
*   Receiver checks sequence number to see if it's a new packet or a retransmission.
*   Handles corrupted ACKs/NAKs and duplicate packets.

## Slide 15: rdt 2.2: a NAK-free protocol

*   rdt 2.2 is a NAK-free protocol.
*   Same as rdt 2.1 but with ACK only
*   Receiver sends ACK for last packet OK. Sender resends if no ACK received.

## Slide 16: rdt 3.0: channels with errors and loss

*   Packets may be lost (or delayed for too long)
*   Sender waits "reasonable" amount of time for ACK
*   **Timeout:** Resend packet if no ACK received in this time.
*   Now, rdt includes:
    * Errors
    * Loss
    * Duplicates

## Slide 17: rdt 3.0 sender

*   A visual example of rdt 3.0 sender works.

## Slide 18: rdt 3.0 receiver

*   A visual example of rdt 3.0 receiver works.

## Slide 19: Performance of rdt 3.0

*   rdt 3.0 is very efficient in small network but not efficient in high-bandwidth network:
*   Example: 1 Gbps link, 15 ms prop. delay, 8000 bit packet implies that the time used is very low.

## Slide 20: Pipelined protocols

*   Instead of sending one packet at a time, send *multiple* packets without waiting for an ACK.
*   This increases utilization of the link.
*   Two basic approaches:
    *   Go-Back-N (GBN)
    *   Selective Repeat (SR)

## Slide 21: Pipelining: increased utilization

*   A visual example of why pipelining works compared to only one packets at a time in term of performance.

## Slide 22: Go-Back-N

*   Sender can have up to N unacknowledged packets in pipeline
*   Receiver only sends cumulative ACK
*   Sender has timer for oldest unacked packet. When timer expires, retransmit all unacknowledged packets.

## Slide 23: GBN: sender extended FSM

*   Visual process of the sender extended FSM.

## Slide 24: GBN: receiver extended FSM

*   Visual process of the receiver extended FSM.

## Slide 25: Selective Repeat

*   Only resend packets that need to be resended.
*   Receiver individually acknowledges all correct received packets
*   Sender maintains timer for each unacked packet
*   Sender retransmits only those packets that have timed out
*   Requires receiver buffering

## Slide 26: Selective repeat: sender, receiver windows

*   Both Sender and receiver have a "window" of sequence numbers.
*   Sender can only send packets within its window.
*   Receiver can only accept packets within its window.

## Slide 27: Selective repeat

*   Sender sends packets within the window and resets timer to each one.
*   Receivers can accept the packet if they are within the window, otherwise will be discarded.
*   Goes back and resent packets when there is timer expired or NAK received.

## Slide 28: Selective repeat (cont.)

*   When send ACK to the clients, reset the timer.
*   Otherwise if the packets out of window, it will be discarded.

## Slide 29: TCP: Overview

*   TCP provides reliable data transfer.
*   Connection-oriented: requires setup between client and server.
*   Pipelined: Allows multiple packets to be sent without waiting for ACK.
*   Flow control: Avoids overwhelming receiver with data.
*   Congestion control: Reduces sending rate when network is congested.

## Slide 30: TCP connection establishment

*   Before exchanging data, sender and receiver "handshake."
*   **Three-way handshake:**
    1.  Client sends a SYN (synchronize) packet to server.
    2.  Server responds with SYNACK (synchronize-acknowledge).
    3.  Client sends ACK. Connection is now established.

## Slide 31: TCP: reliable data transfer

*   Simplified TCP sender (no flow or congestion control, no retransmission of premature timeout, simplified timer handling):

## Slide 32: TCP: retransmission scenarios

*   Three possible causes for the TCP to be retransmitted:
    *  Lost ACKs.
    *  Premature timeout.
    *  Cumulative ACKs.

## Slide 33: TCP cumulative ACK

*   TCP has "cumulative ACKs," meaning an ACK for packet *n* also acknowledges all packets *before* *n*. (A1/A2: Like saying, "I got everything up to number 5").
*   Lost packets results in duplicate ACK which triggers resending.

## Slide 34: TCP fast retransmit

*   When sender receives triple duplicate ACK:
         TCP sender immediately retransmit unacknowledged segment with smallest sequence number.

## Slide 35: TCP flow control

*   Receiver advertises "receive window" (rwnd)
*   Receiver says: "I have this much buffer space left".
*   Sender limits the traffic and does not overwhelm the receiver.

## Slide 36: TCP congestion control

*   Goals:
        *  Fairness
        *  Efficiency

## Slide 37: TCP congestion control: AIMD

*   **AIMD (Additive Increase, Multiplicative Decrease):**
        *  *Increase* congestion window (cwnd) by 1 MSS (Maximum Segment Size) every RTT until loss occurs.
        *  *Decrease* cwnd by factor of 2 after loss.
*   "Sawtooth" behavior: cwnd increases linearly, then drops sharply.

## Slide 38: TCP congestion control: summary

*   Two phases:
         * Slow start.
         * Congestion avoidance.
*   At first, increase exponentially, then increase linearly, then drop multiplicatively.

## Slide 39: TCP throughput: fairness

*   Fairness goal: if K TCP sessions share same bottleneck link of bandwidth R, each should have average rate of R/K

## Slide 40: UDP: more

*   "Best effort" service. (A1/A2: No guarantees)
*   Connectionless: no handshake.
*   Each UDP segment handled independently.
*   Uses: streaming multimedia, DNS, SNMP.

## Slide 41: UDP: more

*   Why use UDP?
    *   No connection establishment (reduce delay)
    *   Simple: no congestion control.
    *   Fine-grained control - application knows best (can build reliability into app)
    *   No connection state