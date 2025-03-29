# CENG 314 - Application Layer: Midterm Study Notes

## Slide 1: Application Layer Overview

*   **Application Layer:** The top layer in the internet model, responsible for network applications (like web browsing, email).
*   **Principles of network applications:**  Rules or concepts on how applications are built to use the network.
*   **Web and HTTP:**  How web pages are sent and received. HTTP is the language used.
*   **E-mail, SMTP, IMAP:**  Protocols used to send (SMTP) and receive (IMAP) email.
*   **DNS (Domain Name System):** Translates website names (like google.com) into IP addresses (like 172.217.160.142).
*   **P2P applications:** Applications where computers share files directly with each other (e.g., BitTorrent).
*   **Video Streaming and Content Distribution Networks:** How videos are delivered efficiently online.
*   **Socket Programming with UDP and TCP:** How programmers create network applications using UDP (fast but unreliable) and TCP (slower but reliable).

## Slide 2: DNS: Domain Name System

*   **DNS (Domain Name System):**  A system that turns easy-to-remember website names into IP addresses that computers use.
    *   Think of it like a phone book for the Internet.
*   **People identifiers:** Like SSN, name, passport #
*   **Internet hosts and routers:** Like IP addresses and "names" for humans.
*   **Distributed database:**  The DNS information is spread across many servers, not just one.
*   **Name servers:** Special computers that store DNS information.
*   **Application-layer protocol:** DNS uses a specific language to talk between computers and DNS servers.
*   **Resolve names:** To find the IP address that matches a website name.
*   **Runs over UDP, port 53:** DNS uses UDP (a type of internet "postman") on port number 53.
*   **Berkeley Internet Name Domain (BIND):** Popular DNS software.

## Slide 3: DNS: Services

*   **Writing URL to the add. bar of browser:** When you type a web address, the browser starts a DNS lookup.
*   **Client side of DNS app is run:** Your computer uses a small piece of software to ask a DNS server for the IP address.
*   **DNS client sends a query:** Your computer asks a DNS server, "What is the IP address for example.com?"
*   **DNS client receives a reply:** The DNS server tells your computer the IP address.
*   **TCP connection between browser and HTTP server:** Your browser connects to the website using the IP address it found.
*   **Caching in nearby DNS servers?:** DNS servers save the answers they find so they can give them out quickly to others that ask.

## Slide 4: DNS: Services (cont.)

*   **Translating hostnames to IP addresses:** The main job of DNS. Other internet protocols (HTTP and SMTP) use this translation.
*   **Host aliasing:** Giving a website multiple names.
    *   **Canonical name:** The "real" name of a website.
    *   **Alias name:** A shorter or easier-to-remember name.
    *   *Example*:  `enterprise.com` and `www.enterprise.com` might both point to the same server, with the first being the alias.
*   **Mail server aliasing:** Similar to host aliasing, but for email servers. The MX record is used for email.

## Slide 5: DNS: Services (cont.)

*   **Load distribution among replicated servers:** DNS can give different IP addresses each time someone asks for a website to spread out the traffic to multiple servers.
*   **Replicated Web servers:** Many servers hosting the same website.
*   **DNS query:** Asks the set of IP addresses, the server rotates the order, spreading usage among them.

## Slide 6: Thinking about the DNS

*   **Humongous distributed database:** DNS is really big and spread out.
*   **Many trillions of queries/day:** DNS gets asked for information *a lot*.
*   **Performance matters:** DNS needs to be fast because almost everything on the internet uses it.
*   **Organizationally, physically decentralized:** Many different groups control parts of the DNS system.

## Slide 7: Thinking About the DNS (cont.)

*   **Centralized Design Problem:** If all names had to go to a single server, issues such as single-point of failure, query handling, significant delays, and maintenance emerge.
*   **Distributed Design Solution:** Mapping across them, and it has three classes: root, top-level domain (TLD), and authoritative

## Slide 8: DNS: A Distributed, Hierarchical Database

*   **Hierarchical Structure:** DNS is organized like a tree.
    *   **Root DNS Servers:**  At the very top.
    *   **Top-Level Domain (TLD) Servers:**  Handle domains like `.com`, `.org`, `.edu`.
    *   **Authoritative DNS Servers:**  The final source of truth for a specific domain (like `amazon.com`).
*   **Client wants IP address for `www.amazon.com`:**
    1.  Ask a root server where to find the `.com` server.
    2.  Ask the `.com` server where to find the `amazon.com` server.
    3.  Ask the `amazon.com` server for the IP address of `www.amazon.com`.

## Slide 9: DNS: Root Name Servers

*   **Root DNS Servers:**
    *   Copies of 13 different root servers.
    *   More than 1000 root servers.
    *   Managed by 12 different organizations.
    *   Coordinated by the Internet Assigned Numbers Authority.
    *   Provide TLD IP addresses.

## Slide 10: Top-Level Domain, and Authoritative Servers

*   **Top-Level Domain (TLD) Servers:**
    *   Responsible for domains like .com, .org, .net, .edu.
    *   Provide IP addresses for authoritative ones.
*   **Authoritative DNS Servers:**
    *   Owned by organizations/companies that host websites.
    *   Provide hostname to IP mappings (records).
    *   Maintained by organization or service provider.

## Slide 11: Local DNS Name Servers

*   **Local DNS name servers:**
    *   Another one not in the hierarchy.
    *   Owned by ISP's (default name server).
    *   Close to host.
*   **When host makes DNS query, it is sent to its local DNS server:**
    *   Local DNS server returns reply, answering:
    *   From its local cache of recent name-to-address translation pairs (possibly out of date!)
    *   Forwarding request into DNS hierarchy for resolution.
    *   Each ISP has local DNS name server; to find yours.

## Slide 12: DNS Name Resolution: Iterated & Recursive Query

*   **Iterative Query:**
    *   The client talks directly to each DNS server, one at a time. The DNS server is responsible for contacting the name server.
*   **Recursive Query:**
    *   The client asks *one* DNS server, and that server does all the work to find the answer. The DNS server is responsible for returning the name server.

## Slide 13: Caching DNS Information

*   **Caching:**  Saving DNS information to use it again quickly.
*   **Caches Mapping:** Any DNS server can save (cache) the website names and their related IP address.
*   **Cache Entries Timeout (TTL):** Saved entries don't last forever. They disappear after a certain amount of time (Time To Live).
*   **Cached entries may be out-of-date:** DNS data can be old/wrong.
*   **Best-effort name-to-address translation:** DNS does its best to find the right IP address.

## Slide 14: DNS Records

*   **DNS Records:** The information stored in DNS servers.

    *   Format: (name, value, type, ttl)
        *   **name:** the hostname
        *   **value:** the IP address
        *   **type:** indicates the type
        *   **ttl:** how long the record is valid
*   **Type=A:** `name` is a hostname, `value` is the IP address. (Most Common)
*   **Type=CNAME:** `name` is an alias, `value` is the *canonical* name. (Website has another name)
*   **Type=NS:** `name` is a domain, `value` is the name of the authoritative name server. (Find the DNS Server)
*   **Type=MX:** `value` is the canonical name for a mail server associated with the alias.

## Slide 15: DNS Records

*   If a DNS server is *authoritative* for a particular hostname, then the DNS server will contain the A record for the hostname.
*   If a DNS server is *not authoritative* for a hostname, then the server will contain the NS records.

## Slide 16 & 17: DNS Protocol Messages

*   **DNS Query and Reply Messages:** DNS servers use these to ask for and give back information.
*   **Same Format:** Both questions and answers use the same basic structure.
*   **Header:**
    *   **Identification:** A number to match questions and answers.
    *   **Flags:**  Tell if the message is a question or an answer, if recursion is wanted, etc.
*   **Questions:** What's being asked.
*   **Answers:** The IP address (or other info) that was found.
*   **Authority:** Information about the servers that gave the answer.
*   **Additional Info:** Extra helpful data.

## Slide 18 & 19: DNS Protocol Messages (cont.)

*   Shows raw data of DNS queries and answers.
*   Includes flags, questions, and answers.

## Slide 20: Getting Your Info Into the DNS

*   **Register your domain name:**
    *   Go to a DNS registrar, like GoDaddy or Network Solutions
    *   You pay them to put your website name and IP address into the DNS system.
*   **Create authoritative server locally with IP address:**
    *   Type A record for www.networkuptopia.com.
    *   Type MX record for networkutopia.com.

## Slide 21: DNS Security

*   **DDoS Attacks:** Trying to break DNS by flooding root servers with traffic.
*   **Spoofing Attacks:** Giving fake DNS answers.
    *   **DNS Cache Poisoning:** Putting wrong information into a DNS server's memory.
    *   **DNSSEC:** Security to prevent DNS spoofing. It checks that the answers are real.

## Slide 22: Application Layer: Overview

*   Same slide as slide 1.

## Slide 23: Peer-to-peer (P2P) architecture

*   **P2P:** Computers share files directly with each other, instead of going through a central server.
*   **Always-on server:** No.
*   **Arbitrary end systems directly communicate:** Yes.
*   **Peers request service from other peers, provide service in return to other peers:** Computers request and provide services.
*   **Self scalability:** The more users join, the faster the network becomes.
*   **Peers are intermittently connected and change IP addresses:** Computers enter/leave, changing the addresses.
*   **Examples:** BitTorrent, streaming (Kankan), VoIP (Skype).

## Slide 24: File distribution: client-server vs P2P

*   **File Distribution:** Sending a file to many people.
*   **Client-Server:**
    *   One computer (the server) sends the file to everyone.
*   **P2P:**
    *   Everyone helps share the file.
*   **Peer upload/download capacity is limited resource:** Server and user capacity.

## Slide 25: File distribution time: client-server

*   **Server Transmission:**  The time it takes the server to send the file to everyone.
*   **Client:** Time for all clients to download the file copy.
*   **Time to distribute file:** Total time for client-server approach.

## Slide 26: File distribution time: P2P

*   **P2P advantage:** Each person assists, which servers assist in distribution.
*   **Server Transmission:**  The time it takes the server to send the file to *at least* one person.
*   **Client:** Time for all clients to download the file copy.
*   **Clients:** Time for aggregate clients to download file.
*   **Time to distribute file:** Total time for P2P approach.

## Slide 27: Client-server vs. P2P: example

*   As the number of peers increases, client-server time increases linearly.
*   While client-server time increases, P2P time is lower than client-server.

## Slide 28: Application layer: overview

*   Same slide as slide 1.

## Slide 29: Video Streaming and CDNs: context

*   **Video Streaming:** Watching videos online.
*   **Major consumer of Internet bandwidth:** Yes.
*   **Challenge:** Reaching many users while handling different internet speeds and devices.
*   **Solution:** Using a distributed network.

## Slide 30: Multimedia: video

*   **Video:** Series of pictures shown quickly.
*   **Digital image:** Array of pixels.
*   **Coding:** Compression by removing extra repeated elements.

## Slide 31: Streaming stored video

*   **Streaming stored video:** Playing a video from a server.
*   **Simple Scenario:** From a video server to client.
*   **Challenges:**
    *   **Varying bandwidth:** Internet speed can change.
    *   **Packet loss:** Data can get lost.

## Slide 32: Streaming multimedia

*   **HTTP streaming:** Sending videos over the web using HTTP.
    *   Video is stored at an HTTP server.
    *   A TCP connection, HTTP request, and responses.
    *   On client, bytes are collected in a client application buffer.
    *   When number of bytes in buffer exceeds a predetermined threshold, the client application begins playback.
*   **Shortcoming:** All clients receive the same encoding of the video.

## Slide 33: Streaming multimedia: DASH

*   **DASH (Dynamic Adaptive Streaming over HTTP):** Video adjusts to your internet speed.
*   **HTTP streaming:** Sending videos over the web using HTTP.
    *   Server:
        *   Video file is divided into chunks.
        *   Each chunk encoded at multiple different rates.
    *   Client:
        *   Periodically estimates server-to-client bandwidth.
        *   Consulting manifest, requests one chunk at a time.
        *   Chooses maximum coding rate available with the current bandwidth.

## Slide 34: Content distribution networks (CDNs)

*   **CDNs:** Networks to help distribute content to millions of users.
*   **Content distribution networks (CDNs):**
*   **Challenge:** Streaming videos to many users.
*   **Option 1:** Single server that does not scale.

## Slide 35: Content distribution networks (CDNs)

*   **Challenge:** Streaming content to simultaneous users?
*   **Option 2:** Store/serve multiple copies of videos at multiple geographically distributed sites (CDN).
*   **Two server placement approaches:** Enter deep and bring home.
*   **Enter deep:** CDN servers are in access networks (access ISP's).
*   **Bring home:** CDN servers are in IXP's.

## Slide 36: Application Layer: Overview

*   Same slide as slide 1.

## Slide 37: Socket programming

*   **Socket Programming:**  Learning how to create programs that communicate over the internet.
*   **Goal:** Learn how to build client/server applications that communicate using sockets.
*   **Socket:**
    *   A "door" between a program and the internet. It's how your code sends and receives data.

## Slide 38: Socket programming

*   **Two socket types:**
    *   **UDP:** Unreliable but faster.
    *   **TCP:** Reliable but a bit slower.
*   **Application Example:**
    *   Client sends data to server.
    *   Server makes the data uppercase.
    *   Server sends the uppercase data back.
    *   Client shows the uppercase data.

## Slide 39: Socket programming with UDP

*   **UDP:**
    *   No "connection" is needed before sending.
    *   No handshake before sending data.
    *   Data can be lost or arrive in the wrong order.
*   **Application viewpoint:**
    *   Transfer of groups of bytes.

## Slide 40: Client/server socket interaction: UDP

*   Show interaction between UDP servers and clients.

## Slide 41: Example app: UDP client

*   Show Python code of UDP clients.

## Slide 42: Example app: UDP server

*   Show Python code of UDP servers.

## Slide 43: Socket programming with TCP

*   **TCP:**
    *   Need a "connection" before sending.
*   **Client must contact server:**
    *   When contacted by client, server TCP creates new socket.
*   **Application viewpoint:**
    *   TCP provides reliable, in-order byte-stream transfer.

## Slide 44: Client/server socket interaction: TCP

*   Show interaction between TCP servers and clients.

## Slide 45: Example app: TCP client

*   Show Python code of TCP clients.

## Slide 46: Example app: TCP server

*   Show Python code of TCP servers.

## Slide 47: General flow

*   Visualizes general flow between clients and servers.

## Slide 48: General flow

*   Visualizes sockets used by the client and the server in TCP communication.