# CENG 314 - Quiz 1 (Section 4) - Study Notes

These notes provide a concise overview of the questions, focusing on key concepts and important terms for studying Quiz 1 - Section 4.

## Question 1: DASH Explanation

*   **DASH (Dynamic, Adaptive Streaming over HTTP):** A way to watch videos online that adjusts to your internet speed.
*   **Server (what the video provider does):**
    *   Divides the video into small pieces (chunks).
    *   Creates different quality versions of each piece (high, medium, low).
    *   Lists all these chunks in a "manifest" file (like a table of contents).
    * Files Replicated in various CDN nodes.

*   **Client (what your device does):**
    *   Checks your internet speed regularly.
    *   Looks at the manifest file.
    *   Requests the right quality chunks based on your speed, one piece at a time.

## Question 2: DNS Hierarchy Responsibilities

*   **Root Name Servers:**
    *   Know the addresses of the Top-Level Domain (TLD) servers.
    *   Provide TLD IP addresses.

*   **Top-Level Domain (TLD) Servers:**
    *   Know the addresses of the Authoritative DNS servers for each TLD (like .com, .org).
    *   Provide IP address for authoritative ones.

*   **Authoritative DNS Servers:**
    *   Hold the actual IP addresses for specific websites (host name to IP mapping).
    *   Provides authoritative hostname to IP mappings (records)

*   **Local DNS Name Servers:**
    *   Close to host
    *   Stores recently accessed requests, this is called caching