# Year 2021 Model Answers

## SECTION A

### Q.1(a): What is computer network? Distinguish between i) Computer vs. autonomous systems ii) Client server model vs. Peer-to-peer communication model.

**Answer:**
**Computer Network:**
A computer network is a structurally interconnected collection of autonomous computers and devices that share resources (like printers or internet access) and exchange information using standard communication protocols over digital interconnections (wired or wireless).

**Distinctions:**
**(i) Computer vs. Autonomous Systems (AS):**
*   **Computer:** A single functional end-device (host) capable of computation and communication on a network.
*   **Autonomous System (AS):** defined strictly as a set of routers under a single technical administration. It uses an Interior Gateway Protocol (IGP) to route packets within the AS, and presents a single unified routing policy to the global Internet.

**(ii) Client-Server Model vs. Peer-to-Peer Model:**
*(Discussed fully in 2023 Q.4a. Briefly: Client-Server is centralized where thin clients rigidly request data from powerful central servers. Peer-to-Peer is decentralized where every node acts interchangeably as both a client and a server, directly sharing resources continuously).*

---

### Q.1(b): What is Ethernet? Discuss different types of network topologies in computer network.

**Answer:**
**Ethernet:**
Ethernet (standardized precisely as IEEE 802.3) is the overwhelmingly dominant ubiquitous technology for Local Area Networks (LANs). It fundamentally defines the wiring, signaling standards, and MAC addressing logic physically at Layer 1 (Physical) and broadly at Layer 2 (Data Link). It traditionally utilizes CSMA/CD for collision management over twisted pair cables, though modern switched Ethernet practically eliminates collisions entirely.

**Different Types of Network Topologies:**
*(Discussed fully previously. Essential forms include:)*
*   **Bus:** Single shared central coaxial backbone. Prone to cascading failure.
*   **Star:** End nodes branching from a central intelligent switch. Modern Ethernet standard.
*   **Ring:** Circular node-to-node token passing. Obsolete.
*   **Mesh:** Interconnected web of nodes providing supreme fault-tolerant redundancy.
*   **Tree/Hybrid:** Branching Star topologies connected via a core Bus spine.

---

### Q.1(c): What do you know about i) Wired and wireless networking ii) Collision domain and broadcast domain.

**Answer:**
**(i) Wired vs. Wireless Networking:**
*   **Wired:** Uses physical guided media (Cat6 Copper, Fiber optics). Guarantees ultra-high strict bandwidth (up to 100 Gbps+ on fiber), severe low latency, and superb physical security against hacking. Lacks physical mobility.
*   **Wireless:** Uses unguided electromagnetic waves (Wi-Fi, 5G). Allows infinite geographical mobility and fast ad-hoc setup. Suffers from signal attenuation, interference, and demands heavy encryption overhead (WPA3) to secure the open air waves.

**(ii) Collision Domain vs. Broadcast Domain:**
*   **Collision Domain:** A localized segment where frames will collide if sent simultaneously. Hubs form one large collision domain. Switches filter packets, forwarding frames only to the necessary segments, meaning switch ports become separate, isolated collision domains.
*   **Broadcast Domain:** A broader segment where a Layer 2 Broadcast safely reaches every host. Switches forward broadcasts across all ports. Only Layer 3 Routers block broadcasts.

---

### Q.1(d): Describe the construction and operation of i) Hub, switch and router ii) Token passing and FDDI.

**Answer:**
**(i) Hub, Switch, and Router:**
*   **Hub (Layer 1 - Physical):** A "dumb" multiport repeater. It rigidly receives a signal on one port and blindly broadcasts it out of completely all other ports. It creates massive single collision and broadcast domains.
*   **Switch (Layer 2 - Data Link):** An intelligent bridging device. It actively learns MAC addresses and builds a MAC Table. When it receives a frame, it inspects the destination MAC and structurally forwards the frame *only* out of the specific port belonging to that destination. It eliminates collisions.
*   **Router (Layer 3 - Network):** Determines the mathematically shortest overarching path between completely different distinct IP networks. It rigidly breaks broadcast domains, aggressively reads IP destination addresses, and utilizes routing tables to safely bounce packets across the internet grid.

**(ii) Token Passing and FDDI:**
*   **Token Passing:** A deterministic channel access method used in Ring networks. A small specialized frame called the "Token" circulates the wire endlessly. A station can purely transmit data *only* if it physically captures the free Token. This structurally prevents all collisions.
*   **FDDI (Fiber Distributed Data Interface):** Extremely robust standard for data transmission on fiber optic lines in LANs. It fundamentally uses a dual-ring (primary and secondary) rotating token-passing architecture. If a fiber cable gets cut, the dual rings instantly fold into a single operational U-turn ring, making FDDI incredibly fault-tolerant against catastrophic physical cable cuts.

---

### Q.2(a): What do you mean by framing? How collision can be handled with CSMA/CD and avoided with CSMA/CA mechanism?

**Answer:**
*(Concepts fully detailed in prior sections).*
*   **Framing** is the systematic Layer-2 process of perfectly encapsulating raw 1s and 0s into structural logical blocks complete with specific Start/Stop flag indicators.
*   **CSMA/CD (Collision Detection):** Used in Ethernet. It relies on random access with no synchronized clocks. Before sending data, stations 'listen' to see if the network is in use. If it is, the station waits. If not, it transmits. If a voltage spike is detected, a collision occurred. They instantly stop, and use Exponential Backoff to wait a random time before retrying.
*   **CSMA/CA (Collision Avoidance):** Used in wireless (802.11). Stations inherently cannot listen while transmitting. They avoid collisions by preceding their data transmission with a formal "Request to Send (RTS)" and "Clear to Send (CTS)" exchange.

---

### Q.2(b): Which OSI layer is used for the following: i) To route packets ii) To run services like FTP and Telnet iii) To detect and correct error iv) To covert packets to frame.

**Answer:**
i) **To route packets:** Network Layer (Layer 3)
ii) **To run services like FTP and Telnet:** Application Layer (Layer 7)
iii) **To detect and correct error:** Data Link Layer (Layer 2) primarily; or optionally Transport Layer (Layer 4) for end-to-end.
iv) **To convert packets to frame:** Data Link Layer (Layer 2)

---

### Q.2(c): Discuss why sliding window protocol is used for flow control. Compare among i) Bit stuffing and byte stuffing methods of framing ii) Go back-N and selective repeat ARQ protocol.

**Answer:**
**Why Sliding Window Protocol is used:**
Elementary "Stop-and-Wait" protocols are disastrously inefficient because the sender essentially spends 90% of its time idling waiting for ACKs. The Sliding Window structurally allows the sender to transmit a consecutive batch of $W$ frames (the window size) rapidly before demanding an ACK. This fundamentally keeps the transmission channel completely saturated, ensuring 100% bandwidth utilization on long, high-speed lines.

**(i) Bit Stuffing vs. Byte Stuffing:**
*   **Byte Stuffing:** Uses completely full special ASCII characters (like `ESC`, `FLAG`) to mark frame ends. If a `FLAG` dynamically appears purely in the data payload, an `ESC` character is forcefully stuffed precisely before it. It is strongly constrained to 8-bit character boundaries.
*   **Bit Stuffing:** Completely agnostic to 8-bit characters. It uses a raw bit sequence (`01111110`). If exactly five continuous `1`s appear naturally in the payload, the transmitter aggressively stuffs a `0` bit to shatter the flag pattern. The receiver destuffs it dynamically.

**(ii) Go-Back-N vs. Selective Repeat ARQ:**
*   **Go-Back-N:** The receiver fundamentally rejects any out-of-order frames. If frame 3 strictly gets corrupted, the receiver drops frames 4, 5, and 6 even if they arrived perfectly. The sender is subsequently forced to "go back" and blindly re-sequence and resend frame 3, 4, 5, and 6. Very wasteful of bandwidth.
*   **Selective Repeat:** The receiver possesses strong buffers. If frame 3 is corrupted, it successfully buffers 4, 5, and 6. It specifically NAKs exclusively frame 3. The sender resends *only* frame 3. Once 3 arrives, the receiver mathematically slides the window past 6. Extremely bandwidth efficient, but demands highly complex internal machine buffering code.

---

### Q.2(d): Find the hamming code for the word "SEE", consider the following ASCII codes: S: 01010011, E: 01000101.

**Answer:**
We construct the Even Parity 7-bit Hamming code for each letter. 7 data bits profoundly require 4 parity bits ($p_1, p_2, p_4, p_8$). Length = 11 bits.
Format: $P_1, P_2, D_3, P_4, D_5, D_6, D_7, P_8, D_9, D_{10}, D_{11}$

**1. Letter 'S' (1 0 1 0 0 1 1):**
*   Data: $D_3=1, D_5=0, D_6=1, D_7=0, D_9=0, D_{10}=1, D_{11}=1$
*   $P_1$ checks 1,3,5,7,9,11 $\rightarrow 1 \oplus 0 \oplus 0 \oplus 0 \oplus 1 = 0 \rightarrow p_1 = 0$
*   $P_2$ checks 2,3,6,7,10,11 $\rightarrow 1 \oplus 1 \oplus 0 \oplus 1 \oplus 1 = 0 \rightarrow p_2 = 0$
*   $P_4$ checks 4,5,6,7 $\rightarrow 0 \oplus 1 \oplus 0 = 1 \rightarrow p_4 = 1$
*   $P_8$ checks 8,9,10,11 $\rightarrow 0 \oplus 1 \oplus 1 = 0 \rightarrow p_8 = 0$
*   **Hamming Code for 'S': `0 0 1 1 0 1 0 0 0 1 1`**

**2. Letter 'E' (1 0 0 0 1 0 1):**
*(Previously completely solved in 2023 Q.2(c))*
*   **Hamming Code for 'E': `1 0 1 0 0 0 0 0 1 0 1`**

**Final output stream for 'SEE':**
`00110100011` `10100000101` `10100000101`

---

### Q.3(a): Describe the TCP 3-way handshaking and TCP congestion control scheme in brief.

**Answer:**
*(3-way handshake fully described in 2022 Q.3(a))*
1. **SYN:** Client requests connection.
2. **SYN-ACK:** Server acknowledges and synchronously requests bi-directional transit constraints.
3. **ACK:** Client solidly confirms. Connection open.

**TCP Congestion Control Scheme:**
TCP aggressively manages network internal congestion mathematically using four distinct, highly controlled phases operating over a dynamically shifting Congestion Window (`cwnd`).
1.  **Slow Start:** The connection strictly begins conservatively (`cwnd = 1` MSS). For every subsequent ACK flawlessly received, the window effectively doubles exponentially ($1, 2, 4, 8 \dots$). It aggressively ramps up speed seamlessly until it hits an assigned Threshold (ssthresh).
2.  **Congestion Avoidance (AIMD):** Once visually past the strict threshold, exponential doubling stops entirely. The window strictly increases additively (increasing monotonically by roughly $+1$ MSS per round trip).
3.  **Fast Retransmit:** If the sender surprisingly receives 3 absolutely duplicate ACKs from the receiver, TCP instantly assumes a single solitary packet safely dropped due to minor congestion. It rapidly retransmits the missing segment seamlessly before waiting for rigid timeouts.
4.  **Fast Recovery:** Following a Fast Retransmit, TCP doesn't completely crash the window back fully to 1. It halves the threshold strictly ($ssthresh / 2$), and logically drops back smoothly into pure Congestion Avoidance to keep line-speed high.

---

### Q.4(c): Why IP is called the connectionless protocol? Compare among transparent and non-transparent segmentation.

**Answer:**
**Why IP is Connectionless:**
Internet Protocol (Layer 3) is utterly connectionless because it deliberately does not establish, negotiate, or rigidly maintain any formal circuit or path mathematically before sending data. Every single IP packet routed into the internet core acts completely independently. They may explicitly traverse vastly different dynamic physical router paths to get to the same destination, and they might consequently arrive completely out of mathematical order. It strictly leaves complex reliability and strict connection management entirely to the higher Transport layer (TCP).

**Transparent vs. Non-Transparent Segmentation (Fragmentation):**
When a massive packet definitively hits a network link with a tiny structural MTU boundary, it must be thoroughly broken structurally.
*   **Transparent Fragmentation:** An intensely hidden, localized structural approach. A massive packet is shattered tightly by a router upon entering a small-MTU ATM backbone framework. However, the exit-edge router of that specific tiny backbone structurally identically reassembles the fragments completely *before* it gets sent to the rest of the wider internet. The outside world transparently has no idea it was ever internally fragmented.
*   **Non-Transparent Fragmentation:** The standard strict IPv4 global approach. When a router forcibly fragments a large packet, the independent fragments structurally remain utterly shattered for the entire remaining geographic journey. Specifically, solely the final ultimate destination host computer aggressively shoulders the burden of definitively reassembling the scattered fragments.
