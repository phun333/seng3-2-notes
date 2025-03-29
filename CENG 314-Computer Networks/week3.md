# CENG 314 - Application Layer (Week 3) - Study Notes

These notes provide a concise overview of the Application Layer, focusing on key concepts and important terms for midterm preparation.

## Slide 1: Application layer: overview

*   Overview of different topics within this layer.
    *   **Principles of network applications:**  Basic rules about how network programs are created.
    *   **Web and HTTP:** Discussing how to create Web application using HTTP.
    *   **E-mail, SMTP, IMAP:** Creating an emailing service.
    *   **The Domain Name System (DNS):** How to translate website names into computer addresses.
    *   **P2P applications:**
    *   **Video streaming and content distribution networks:** How to distribute the videos over the network.
    *   **Socket programming with UDP and TCP:** How to connect a program with UDP or TCP connection.

## Slide 2: Some network apps

*   Examples of network applications.
    *   Social networking
    *   Web
    *   Text messaging
    *   Email
    *   Multi-user network games
    *   Streaming video.
    *   P2P file sharing
    *   Real-time video conferencing
    *   Internet search
    *   Remote login

## Slide 3: Creating a network app

*   When creating a network application, we use the existing computer networks but we do not have to write a network-core devices
*   Applications that run on the edge system allows for rapid app development, propagation.

## Slide 4: Creating a network app

*   Have an application plan (architecture) before starting coding
*   application's architecture is different from the network architecture.
*   For a developer, the network architecture is already done.
*   Architectures: Client-server and peer-to-peer (P2P).

## Slide 5: Client-server paradigm

*   **Server:** A computer that's always on and available with a fixed address.
*   **Client:** Contacts the server for services.
*   Clients contact the server for some functionalities/services, and it does not directly communicate with each other
*   Examples: HTTP, IMAP, FTP.

## Slide 6: Peer-peer architecture

*   No dedicated server, all computers are equal ("peers").
*   End systems communicate directly.
*   Self-scalability: new peers bring new service capacity
*   Peers are intermittent and change IP addresses

## Slide 7: Processes communicating

*   First, understand how programs running communicate with each other.
*   Processes: the program running in a host
*   Different processes communicate with each other using messages across the network.

## Slide 8: Processes communicating

*   **Process:** A program that is running on a device.
*   Different host processes communicate by exchanging messages.
*   **Client process:** The process that starts a conversation.
*   **Server process:** The process that waits to be contacted.

## Slide 9: Sockets

*   Processes send and receive messages through a "socket."

*   **Socket:** An interface between the application layer and the transport layer in the application system.
*   A process can be considered a house, and the socket the door to the outside of the house.
*   Each communication have two sockets: one in the client and one in the server.
*   Socket relies on infrastructure for transportation.

## Slide 10: Addressing processes

*   Processes must have an "identifier" (IP address and port number) to receive messages.
*   **IP address:** Each host has a unique IP address to distinguish them.

*   **Identifier:** It includes both IP address and port numbers associated with process on host.

## Slide 11: An application-layer protocol defines

*   Defines how processes send and respond to messages.
    *   Types of messages (request, response).
    *   Message syntax
    *   Rules

*   **Open protocols:** Standards that everyone can use. (Defined in RFCs) HTTP, SMTP
*   **Proprietary protocols:** Protocols owned by companies.  Skype, Zoom

## Slide 12: What transport service does an app need?

*   Need to choose the protocols to use for our application.
*   Things to consider:
    *   **Reliability:**  Will data be delivered correctly?
    *   **Timing:** Does it matter how long it takes?
    *   **Throughput:** How much data needs to be sent?
    *   **Security:** Does the application need encrypted connection?

## Slide 13: Transport service requirements: common apps

*   Examples of common apps and what they need from the transport layer.

## Slide 14: Internet transport protocols services

*   **TCP service:** Reliable transport, flow control, congestion control, connection-oriented. *Does not* provide timing, minimum throughput, security.

*   **UDP service:** Unreliable data transfer. *Does not* provide reliability, flow control, congestion control, timing, throughput guarantee, security, connection setup.

## Slide 15: Internet applications, and transport protocols

*   Examples of application layer protocols and what type of transport they use

## Slide 16: Securing TCP

*   Vanilla TCP and UDP sockets does not provide any security features
*   Apps uses TLS (Transport Layer Security) libraries to use encrypted connection.

## Slide 17: Application layer: overview

*   Recap of topics that has been overviewed.

## Slide 18: Web and HTTP

*   Defines how web applications process pass message to each other.
*   HTTP: The set of rules ("protocol") for how web browsers and servers talk to each other.
*   A "web page" consists of several files and HTML files

## Slide 19: HTTP overview

*   **HTTP:**  "HyperText Transfer Protocol" - the protocol for the web.
*   Client/Server model:
*   Client = the browsers that we use to display web objects.
*   Server = Web server that sends information to clients.

## Slide 20: HTTP overview (continued)

*   **HTTP uses TCP**
*   HTTP is stateless. It maintains no information about past client requests.
*   If client sends same requests twice, the server will resend the object.

## Slide 21: HTTP connections: two types

*   **Non-persistent HTTP:**
    *   Opens a TCP connection for *each* object.
    *   Must create and close connections multiple times to download objects.
*   **Persistent HTTP:**
    *   Opens a TCP connection once.
    *   Can send *multiple* objects over that connection.

## Slide 22: Non-persistent HTTP: example

*   A step by step process to how to client initiates HTTP and downloads objects over a TCP connection.

## Slide 23: Non-persistent HTTP: example (cont.)

*   More details on how the process works from the example in the last page

## Slide 24: Non-persistent HTTP: response time

*   **RTT (Round-Trip Time):** The time it takes for a small packet to go from client to server and back.
*   HTTP response time (per object):
    *   One RTT to make TCP connection.
    *   One RTT to send HTTP request and get first bytes.
    *   Object/file transmission time

## Slide 25: Persistent HTTP (HTTP 1.1)

*   Default in most browsers.
*   Server leaves connection open after sending response
*   Client sends request as soon as it sees the objects
*   Allows one RTT to send all referenced objects.

## Slide 26: HTTP request message

*   Two types of HTTP messages: Request and Response.
*   Message is in ASCII format

## Slide 27: HTTP request message: general format

*   General format for the HTTP messages.

## Slide 28: Other HTTP request messages

*   **POST:** Sending data *to* the server (like submitting a form).
*   **GET:**  Getting data *from* the server (usually a specific file).
*   **HEAD:** Server responds with an HTTP message but it leaves out the requested object
*   **PUT:** Uploads new file to the server
*   **DELETE:** Delete the object on the server

## Slide 29: HTTP response message

*   Contains info sent *from* the server *to* the client.
*   Has three sections: Status line, header line, and the entity body

## Slide 30: HTTP response status codes

*   Status codes appear in first line of message.
*   **200 OK:** Request was successful.
*   **301 Moved Permanently:** Requested file is now at a different location.
*   **400 Bad Request:** the request msg was not understood by the server.
*   **404 Not Found:** File not found.
*   **505 HTTP Version Not Supported:**

## Slide 31: Maintaining user/server state: cookies

*   "Cookies" let websites track users and remember things about them.

## Slide 32: Maintaining user/server state: cookies

*   Shows how the cookies works

## Slide 33: Web caches (proxy)

*   "Web caches" store copies of web pages so they can be delivered faster. This reduces traffic to the originating server.
*   Recieves the object, stores a copy in its local storage
*   Sends all the requests from the browser to the cache

## Slide 34: HTTP/2

*   Decreased delay in multi-object HTTP requests
*   Increased flexibility at server in sending objects to client.
*   The server sends the Web page to client over single TCP connection.

## Slide 35: HTTP/2: mitigating HOL blocking

*   HTTP 1.1 clients have to requests the whole page before sending it

## Slide 36: HTTP/2: mitigating HOL blocking

*   HTTP 2 divides objects into frames so it can be interleaved after sending one frame from the video clip.

## Slide 37: Application layer: overview

*   Recap of what has been overviewed

## Slide 38: E-mail

*   Three main components:
    *   **User agents:** (Mail reader) How users read and send email (like Outlook).
    *   **Mail servers:**  Store and send mail messages.
    *   **SMTP:**  The protocol used to send mail between servers.

## Slide 39: E-mail: mail servers

*   **Mailbox:** Contains incoming messages
*   **Message queue:** Stores the outgoing messages
*   The messages are sent between client and receiving server via SMTP protocol.

## Slide 40: SMTP RFC (5321)

*   Uses TCP to transfer the message
*   Sending server sends the mail to receiving server
*   Three phases of transfer:
    *   SMTP handshaking (greeting)
    *   SMTP transfer of messages
    *   SMTP closure
*   Commands/Response interaction: Like HTTP, uses status code and phrases to communicate with the client

## Slide 41: Scenario: Alice sends e-mail to Bob

*   Explains how email flows from the sender to receiver: Alice composes and sends message, Alice's mail server places message into message queue, SMTP connection is opened with Bob's mail server, Alice message is transferred over TCP, message is placed in Bob's mailbox, and he reads them.

## Slide 42: Sample SMTP interaction

*   Examples of commands used during communication

## Slide 43: Mail message format

*   Format of e-mail message
*   **SMTP:** The rules for *exchanging* email.
*   **RFC 2822:** The rules for the *message itself* (like HTML for web pages). The data that will be exchanged

## Slide 44: Retrieving email: mail access protocols

*   **SMTP:** For *sending* mail.
*   **IMAP:** For *retrieving* mail from a server. Messages are stored on a server and can be accessed remotely.