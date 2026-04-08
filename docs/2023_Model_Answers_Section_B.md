### SECTION B

### Q.5(a): What is the difference between connection-oriented and connectionless service? Mention applications of each.

**Connection-oriented Service:**
*   **Definition:** Analogous to the telephone system. It requires communication entities to use a handshake process to establish a connection before sending data. TCP provides connection-oriented services.
*   **Properties:** Transmits data as a continuous stream of bytes. Reliability is strictly achieved by having the recipient acknowledge each message. Packets are received in order due to sequencing and flow control. Uses virtual circuit switching. It is vulnerable to router failure along the dedicated path.
*   **Application Examples:** File transfer (FTP), remote login (Telnet, SSH), and video on demand. These require guaranteed, ordered delivery.

**Connection-less Service:**
*   **Definition:** Analogous to the postal system. Packets of data (datagrams) are transmitted from source to destination directly without establishing a connection. UDP and IP provide connectionless service.
*   **Properties:** Handles packets individually. Each packet carries a full destination address. Packets do not follow a fixed path and can arrive out of order. It is robust to router failure since alternate paths can be taken dynamically.
*   **Application Examples:** Credit card point-of-sale verification, electronic funds transfer, remote database access queries, DNS. These are inherently query/reply where speed and robustness are preferred over sustained stream overhead.

---

### Q.5(b): What does a NAT do? Explain with functionality and translation table format.

**What NAT Does:**
Network Address Translation (NAT) allows a single device (like a router) to act as an agent between a local private network and the public Internet. It maps multiple private non-routable IP addresses to a single public IP address, largely solving the IPv4 address exhaustion problem.

**Functionality and Translation Process:**
*   Implementation acts as a proxy: A NAT router maintains an **address translation table**.
*   **Outgoing packets:** The NAT router replaces the `(Source IP, Source Port)` of every outgoing datagram from the private host with its own `(NAT Public IP, New Port)`.
*   The router remebers this mapping by logging the translation pair in its table.
*   **Incoming packets:** When the remote server responds to the `(NAT Public IP, New Port)`, the NAT router looks up that specific port in its translation table, replaces the destination IP/Port in the packet header with the original private `(Source IP, Source Port)`, and forwards it to the correct internal host.

**Translation Table Format Example:**

| Private Connection Side | Public / WAN Side | Remote Target |
| :--- | :--- | :--- |
| `192.168.1.50:3211` | `203.0.113.5:60001` | `104.21.3.4:80` |
| `192.168.1.65:5432` | `203.0.113.5:60002` | `8.8.8.8:53` |

---

### Q.5(c): Run Dijkstra algorithm and show steps to find shortest path from appropriate router.

*(Note: Since no specific graph is provided in the general exam template, this outlines the standard Link State algorithmic steps expected for Dijkstra's implementation.)*

**Dijkstra's Shortest Path Algorithm (Link State):**
1.  **Initialization:** The chosen source router (e.g., node A) initializes the cost to itself as 0 and the cost to all other unknown routers as Infinity (∞).
2.  **Neighbor Assessment:** The source node examines all its directly connected neighbors. It updates their path costs based on the link state weight (cost) of connecting to them.
3.  **Select Minimum:** The node selects the unvisited neighbor with the lowest total path cost from the source and marks it as 'visited'.
4.  **Path Relaxation:** From that newly visited node, examine its unvisited neighbors. If the path from the source through this new node to a neighbor is strictly lesser than previously recorded estimated costs, update the routing table with the new, shorter path.
5.  **Iteration:** Repeat this greedy selection and relaxation process until all nodes in the network are marked as visited. The result is a shortest-path spanning tree from the source to every other router in the topological database.

---

### Q.6(a): Mention count to infinity problem related to distance vector routing.

**Count to Infinity Problem:**
Distance Vector routing protocols (like RIP, using the Bellman-Ford algorithm) suffer from the "Count to Infinity" problem due to slow convergence and routing loops.
*   **The Issue:** When a link breaks or a network goes completely down, routers take a very long time to realize the path is truly dead. Because routers only share vectors with their immediate neighbors, bad news travels very slowly. 
*   **The Loop:** If Router X goes offline, Router Y might update its table pointing to Router Z (thinking Z has an alternate path to X). But Z was actually routing to X *through* Y. Y and Z will infinitely cross-update each other, incrementing their "hop count" distance +1 each time, causing packets to bounce in a loop.
*   **The Resolution:** The network increments the distance metric indefinitely until it reaches a defined maximum metric (e.g., 16 hops in RIP) which equates to "Infinity", at which point the route is finally dropped. Techniques like "Poison Reverse" and "Split Horizon" are implemented to mitigate this loop.

---

### Q.6(b): Compare different properties between UDP and TCP.

| Property | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
| :--- | :--- | :--- |
| **Connection Type** | Connection-oriented (requires 3-way handshake) | Connectionless (sends immediately) |
| **Reliability** | Highly reliable. Ordered delivery guaranteed. | Best-effort delivery. Unreliable. |
| **Error Checking** | Explicit Acknowledgements (ACK), checksums, retransmission of lost segments. | Only basic header checksum. Missing datagrams are explicitly dropped. |
| **Flow & Congestion**| Strict Flow control (sliding window) and Congestion control algorithms. | No flow control. No congestion control. |
| **Header Size** | 20 bytes (minimum) | 8 bytes |
| **Transmission** | Byte-oriented data stream | Message-oriented independent datagrams |
| **Use Cases** | File transfer (FTP), Web browsing (HTTP), Email (SMTP, IMAP) | Streaming video, VoIP, DNS, Gaming |

---

### Q.6(c): Between leaky bucket and token bucket traffic shaping algorithms, which one gives better performance? Why?

**Superiority of Token Bucket:**
The **Token Bucket algorithm** provides better overall network performance and flexibility compared to the Leaky Bucket algorithm.

**Why (Based on Implementation Differences):**
*   **Handling Burstiness:** An important difference is that Leaky Bucket enforces a very rigid pattern on the output stream, discarding packets immediately when the bucket is full. It forces bursty traffic to smooth out entirely into a fixed, constant rate. 
*   **Permitting Capacity:** Token bucket is less restrictive. It permits burstiness but bounds it. It collects tokens generated at a regular rate. Packets waiting in a queue must grab a token before being transmitted. If a sudden burst of data arrives and the bucket has saved up tokens, those bursts of packets can be sent all at once.
*   **Discard Policy:** Token bucket throws away excess *tokens* when the bucket is full, but never drops the actual user *packets* (they simply wait in queue until new tokens generate). Leaky bucket drops *packets* when full. Thus, token bucket adapts far better to the bursty nature of modern web traffic without causing data loss.

---

### Q.7(a): Discuss "flow control" and "congestion control".

*   **Flow Control:** This is a vital mechanism regulating the transmission of data strictly between two end devices (Sender and Receiver). It considers only what is going on within that specific session. Its primary goal is to ensure a fast sender does not overwhelm a slow receiver. It is managed by advertising a receive window size.
*   **Congestion Control:** This operates globally. It regulates the flow of packets coming into the network as a whole, preventing the entire network fabric (routers and links) from becoming overloaded. Its goal is to prevent network saturation, dropped packets, and transmission delays across all users.
*   *Interaction:* In TCP, the Effective Window Size (the actual amount of data the source can send) is dictated by taking the mathematically stricter of the two: `MIN(CongestionWindow, AdvertisedWindow)`.

---

### Q.7(b): What are the primary differences between virtual circuit and datagram packet switching?

**Virtual Circuit Packet Switching:**
*   Operates like circuit switching dynamically. Before data flows, a virtual path is established edge-to-edge.
*   Each packet contains a Virtual Circuit Identifier (VCI) in its header.
*   **Routing Decision:** No complex routing decisions are required at each node; routers simply look up the VCI and forward along the pre-established path.
*   Provides Quality of Service (QoS), guaranteed sequential delivery, and minimal per-packet processing delay, but is highly vulnerable to link failure (the whole circuit drops).

**Datagram Packet Switching:**
*   Operates purely connectionless. Every packet carries full source and destination IP addresses.
*   **Routing Decision:** Routing decisions are deeply made dynamically for each individual datagram at every single router hop.
*   Datagrams can follow entirely different routes to the destination and arrive out of order.
*   Highly robust. If a router malfunctions, datagrams simply route around the failure dynamically.

---

### Q.7(c): Name the four layers of the TCP/IP protocol suite along with brief description.

The Internet protocol suite (commonly known as TCP/IP or DoD model) consists of four abstraction layers:

1.  **Application Layer:** Contains all protocols for specific data communications services on a process-to-process level. Ensures network services are available to applications (HTTP, FTP, SMTP, DNS).
2.  **Transport Layer:** Handles host-to-host communication. It establishes logical end-to-end connections managing flow control, reliability, and segmentation (TCP, UDP).
3.  **Internet Layer (Network):** Handles connecting independent networks and establishing internetworking. Specifies how data should be formatted, addressed, and routed to the destination (IP, ICMP, ARP).
4.  **Network Access (Link Layer):** Contains communication technologies for a single physical network segment. It combines OSI Data Link and Physical layers, handling framing, MAC addressing, and hardware interfacing (Ethernet, Wi-Fi, PPP).

---

### Q.8(a): Briefly write about mathematics of transposition cipher with formula.

**Transposition Cipher Mathematics:**
A transposition cipher does not substitute characters; rather, it performs a permutation (reordering) on the plaintext characters.

*   **Key:** In a transposition cipher, the encryption key is explicitly the mathematical rule defining the permutation of character positions. Let the message length be $L$. A permutation pattern is defined over a block size $b$. Let permutation function be $f(i)$.
*   **Encryption:** The cipher function takes the plaintext character at position $i$ and moves it to a new position $j = f(i)$.
    $C[f(i)] = P[i]$
*   **Decryption:** The receiver uses the inverse mathematical permutation using the same block length. 
    $P[i] = C[f^{-1}(i)]$
*   Example: In a Rail Fence or columnar transposition, the exact geometry of rows/columns dictates the mathematical permutation array utilized.

---

### Q.8(b): Draw a labeled block diagram exhibiting DHCP process. Why do we need the DHCP process?

**Why DHCP Process is Needed:**
Dynamic Host Configuration Protocol (DHCP) automatically provides vital network configuration information (IP address, subnet mask, gateway address) to hosts on lease. Connecting a host manually is highly prone to mistakes (e.g., administrator assigns an already used IP address causing IP conflicts). DHCP dynamically distributes these parameters perfectly, allowing devices to freely log on, move between networks, and request temporary configuration without any manual human intervention.

**DHCP DORA Process:**
*   **D - DHCPDISCOVER:** A new node connects and broadcasts (to `255.255.255.255`) requesting an IP. Source IP is `0.0.0.0`.
*   **O - DHCPOFFER:** The DHCP Server picks an available IP and unicassts/broadcasts a proposed offer (IP, lease time) back to the client.
*   **R - DHCPREQUEST:** The host selects the offer and officially broadcasts an acceptance to the network to claim it.
*   **A - DHCPACK:** The Server officially acknowledges the claim and marks the IP as unavailable in its storage.

*(See diagram in the final document: DHCP DORA Process)*

---

### Q.8(c): Find the basic differences between a standard ACL and an extended ACL. What is the basic configuration command?

**Functional Differences:**
*   **Standard ACL:** Can act only based on the **Source IP** address. It either blocks or permits all traffic from that source entirely. Because it does not check destinations, it should generally be placed as close to the destination router as possible to avoid dropping traffic intended for other locations unnecessarily.
*   **Extended ACL:** highly granular. It can filter traffic based on **Source IP, Destination IP, Protocol (TCP, UDP, ICMP), and Port Numbers**. Because it is highly specific, these should be placed as close to the source router as possible to block unwanted traffic before it consumes bandwidth traversing the network.

**Basic Configuration Commands (Cisco syntax):**
*   **Standard ACL (Number range 1-99):**
    `access-list 10 deny host 192.168.1.5`
    `access-list 10 permit any`
    *(To apply)*: `ip access-group 10 in`
*   **Extended ACL (Number range 100-199):**
    `access-list 110 permit tcp 192.168.0.0 0.0.0.255 host 10.0.0.5 eq 80`
