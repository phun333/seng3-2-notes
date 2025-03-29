# CENG 314 - Quiz 1 (Section 3) - Study Notes

These notes provide a concise overview of the questions provided, focusing on key concepts and important terms.

## Question 1: HTTP Request Analysis

*   **1.a) What is the URL of the object requested by the browser?**
    *   The full web address requested.
    *   **lectures.ce.ankara.edu.tr/COM3032/midterm_exam.html**

*   **1.b) What version of HTTP is the browser running?**
    *   The version of the HTTP protocol being used.
    *   **HTTP/1.1**

*   **1.c) What is the IP address of the host on which the browser is running?**
    * You can't tell from the request
    *   **Not Determinable:** The IP address is not part of the HTTP request content shown.

## Question 2: DNS Resolution

*   Scenario: You (quiz.ostim.edu.tr) query for www.quiz.com, using dns.ostim.edu.tr as your local DNS server.
*   Explain Iterative and Recursive DNS resolution.

### Iterative Query:

1.  Requesting Host (quiz.ostim.edu.tr) queries Local DNS server (dns.ostim.edu.tr)
2.  Local DNS queries Root DNS Server
3.  Root DNS Server responds with the address of a TLD DNS Server (e.g., a server for .com)
4.  Local DNS queries the TLD DNS Server
5.  TLD DNS server Responds with the address of Authoritative DNS server for quiz.com
6.  Local DNS queries Authoritative DNS Server (dns.quiz.com)
7.  Authoritative DNS Server responds with the IP address of www.quiz.com
8.  Local DNS returns the IP address of www.quiz.com to requesting host (quiz.ostim.edu.tr)

### Recursive Query:

1.  Requesting Host (quiz.ostim.edu.tr) queries Local DNS server (dns.ostim.edu.tr)
2.  Local DNS queries Root DNS Server
3.  Root DNS Server queries TLD DNS Server
4.  TLD DNS Server queries Authoritative DNS Server (dns.quiz.com)
5.  Authoritative DNS Server
6.  All data passed and cached by previous DNS
7.  Local DNS get the IP address of www.quiz.com
8.  Local DNS returns the IP address of www.quiz.com to requesting host (quiz.ostim.edu.tr)