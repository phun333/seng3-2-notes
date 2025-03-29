# CENG 314 - Transport Layer: Midterm Study Notes (Multiplexing, UDP, TCP)

## Slide 1: Transport Layer: Overview

*   **Transport Layer:** This is the layer between application and network. It sends communication to the application processes.

*   **Transport services and protocols:** The specific rules and methods used to move data at this layer (TCP, UDP).
*   **Multiplexing and demultiplexing:** Giving one sender different sockets, and one receiver getting different sockets.
*   **Connectionless transport: UDP:** UDP is a service that doesn't guarantee delivery of data and is fast.
*   **Connection-oriented transport: TCP:** TCP is a service that guarantees delivery and sets up the connection.
*   **TCP Congestion Control:** How TCP manages network traffic.
*   **Evolution of transport-layer functionality:** How protocols improve to meet needs.

## Slide 2: Transport Services and Protocols

*   **Logical communication:** It is as if hosts are directly connected, but is not directly done.
*   **Physical infrastructure:** Physical infrastructure is between hosts but are not a concern for application processes.
*   **TL protocols in end systems:** Transport layer protols in the end system.
*   **Transport protocols in end systems:**
    *   Sender breaks data into segments and passes into network layers
    *   Receiver reassembles segments into messages and passes into the application layer
*   **Available Internet Applications:** TCP and UDP

## Slide 3: Chapter 3: Roadmap

*   Lists key topics to be covered in the chapter: Transport, Multiplexing, UDP, TCP and other protocols.

## Slide 4: Multiplexing/Demultiplexing

*   **Multiplexing (at sender):** Taking data from multiple applications and putting them into one stream to send over the network.
    *   *Analogy:* Like different people putting their letters into the same mailbox.
*   **Demultiplexing (at receiver):** Taking one stream of data and separating it out to the correct applications on the receiving end.
    *   *Analogy:*  Like the post office sorting letters to the right houses. Header info will deliver received segments to the correct socket.

## Slide 5: How Demultiplexing Works

*   **IP datagrams:** Each IP Datagram has the sender and the receiver.
*   **IP and Port Numbers:** Each is 32bits.
*   **Src Port and Dest Port Number:** Receiving hosts uses the IP address and the port number to direct segments to the appropriate socket.

## Slide 6: Connectionless Demultiplexing: An Example

*   Shows how data segments are directed to the right port and applications on the receiving side.

## Slide 7: Connection-Oriented Demultiplexing: Example

*   Shows a similar concept of demultiplexing, but for TCP.
*   TCP demultiplexing considers more of sender's IP + destination IPs.

## Slide 8: Chapter 3: Roadmap

*   Lists key topics to be covered in the chapter: Transport, Multiplexing, UDP, TCP and other protocols.

## Slide 9: UDP: User Datagram Protocol

*   **UDP:** A simple and fast transport protocol that doesn't guarantee delivery.
*   **"No frills":** Means simple, with not much extra work.
*   **"Best effort":** UDP does what it can, but data may be lost or arrive in the wrong order.
*   **Connectionless:** No need to setup a connection first.
*   **Why UDP?:**
     *   Why is there a UDP, no connection state, can blast away as fast, desired and can function in the face of congestion

## Slide 10: UDP: User Datagram Protocol

*   **UDP is good for:**
    *   Streaming videos.
    *   DNS
    *   SNMP
    *   HTTP/3
*   **Reliable transfer needed?:** If you need to guarantee that data is sent correctly over UDP, then add the reliable transfer at the application layer and add congestion control at the application layer.

## Slide 11: UDP: User Datagram Protocol \[RFC 768]

*   This slide shows the RFC standard used.

## Slide 12: UDP Segment Header

*   **UDP Header:** The extra information added to the data by UDP.
    *   **Source Port:** The application sending the data.
    *   **Destination Port:** The application that should get the data.
    *   **Length:** How big the whole UDP packet is.
    *   **Checksum:** A way to check if the data was changed during sending.
        *   *Analogy:* Like a small math problem the receiver does to make sure the data is correct.
*    Data to/from application layer

## Slide 13: UDP Checksum (Error Detection)

*   **UDP Checksum:** Detects errors and flipped bits.

## Slide 14: Internet Checksum: An Example

*   An example on how the receiver end does an algorithm to compare.

## Slide 15: Chapter 3: Roadmap

*   Lists key topics to be covered in the chapter: Transport, Multiplexing, UDP, TCP and other protocols.

## Slide 16: TCP: Overview

*   **TCP:** A reliable, connection-oriented protocol that guarantees data delivery.
*   **Point-to-point:** One sender, one receiver.
*   **Reliable:** Guarantees data will arrive correctly.
*   **Full duplex:** Data can flow both ways.
*   **Cumulative ACKs:**
   * cumulative ACK's mean they're reporting that they've received all byes.
*   **MSS:** Max segment size is generally around 1460.
*   **Pipelining:** TCP does congestion and flow control.
*   **Flow controlled:** Receiver prevents overwhelming.
*   **Handshaking:** Exchange control messages.

## Slide 17: TCP Segment Structure

*   **TCP Header:** Information at the start of each TCP packet.
    *   **Source Port:** Application sending data.
    *   **Destination Port:** Application receiving data.
    *   **Sequence Number:** The order of data.
    *   **Acknowledgement Number:** Confirming that data was received.
    *   **Receive Window:** How much data the receiver can accept.
    *   **Checksum:** Error checking.

## Slide 18: TCP Sequence Numbers

*   **Sequence Numbers:** The order of data.
*   **Size of Data:** 500,000 bytes.
*   **MSS:** 1000 bytes.
*   **TCP Constructs:** 500 segments of data.
*   Example is given on when the seq is 0, 1000 and so on.

## Slide 19: TCP ACKs

*   **ACKs (Acknowledgements):** A way for the receiver to tell the sender that data arrived correctly.

## Slide 20: TCP ACKs

*   Explains Cumulative ACKs and receiving of bytes.

## Slide 21: TCP Round Trip Time, Timeout

*   **RTT:** The time taken to acknowledge the first segment sent.
*   **Timeout Interval:** How long the sender waits for an acknowledgement before resending data.

## Slide 22: TCP Round Trip Time, Timeout

*   **Timeout:** Setting timeout for RTT.

## Slide 23: TCP Sender (Simplified)

*   Details how TCP data received has been created.

## Slide 24: TCP: Retransmission Scenarios

*   **Retransmission: If ack is lost** If the ack is lost, there's another copy where the segment is transmitted.
*   **Premature timeout:** An early timeout, two segments acknowledged.

## Slide 25: TCP: Retransmission Scenarios

*   **Retransmissions in case if first ACK is lost,** second ACK covers it.

## Slide 26: TCP Fast Retransmit

*   **Fast Retransmit:** Retransmit if it gets 3 duplicate acknowledgements, a missing segments is likely.

## Slide 27: TCP Flow Control

*   **Flow Control:** Preventing the sender from sending data too fast for the receiver to handle.
*   **Matching the rates:** The sender has to match against the rate that the receiving application.

## Slide 28: TCP Flow Control

*   TCP sender maintains a window, called the receive window, it gives the sender an idea of how much buffer to use.

## Slide 29: TCP Connection Management: TCP 3-Way Handshake

*   The three-way handshake

## Slide 30: Closing a TCP Connection

*   Closing the connection.

## Slide 31: TCP States - Client Side

*   TCP has various states, depending on how long each side takes.

## Slide 32: TCP States - Server Side

*   TCP has various states, depending on how long each side takes.