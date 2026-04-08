## Year 2020 Model Answers

### SECTION A

### Q.1(a): Why Internet is called a network of networks? Justify. What is the relation between Internet and computer network? What are the components of computer network?

**Why the Internet is called a "network of networks":**
The Internet is not a single, monolithic network owned by one entity. Rather, it is a massive, worldwide system composed of thousands of individual, disparate autonomous networks (such as university LANs, corporate WANs, and regional ISPs) that are seamlessly interconnected. It mathematically links these independent networks together using a common suite of standard protocols (TCP/IP), functioning globally as a single, cooperative, and self-sustaining communicative facility.

**Relation between Internet and Computer Network:**
A "computer network" is the foundational building block. It is a localized collection of connected computers sharing physical resources (like a single office LAN). The "Internet" is strictly the overarching infrastructure that physically and logically connects millions of these isolated computer networks together over vast geographical distances.

**Components of a Computer Network:**
The basic structural building blocks include:
1.  **End Devices (Hosts):** PCs, servers, smartphones.
2.  **Network Devices (Nodes):** Switches, Hubs, Routers, Access Points.
3.  **Transmission Media:** Guided (Twisted pair, Coaxial cable, Fiber optics) or Unguided (Radio waves, Microwaves).
4.  **Protocols:** The mathematically defined rules governing data format and transmission (e.g., TCP/IP, Ethernet IEEE 802.3).

---

### Q.1(b): What do you know about unicast, broadcast, and multicast mode of communication? Compare among different types of network topologies in computer network with their pros and cons.

**(i) Modes of Communication:**
*   **Unicast:** Communication is strictly one-to-one. A single sender transmits a message directed exclusively to a single, specific receiver MAC/IP address.
*   **Multicast:** Communication is strictly one-to-many. A sender transmits a single message that is intelligently routed only to a specific, subscribed group of receivers (e.g., IPTV).
*   **Broadcast:** Communication is strictly one-to-all. A sender transmits a message meant to be received and processed by absolutely every single device physically present on the local subnet.

**(ii) Comparison of Network Topologies:**
*(Summarized from previous detailed answers)*
*   **Bus:**
    *   *Pros:* Simple layout, requires the least amount of cabling.
    *   *Cons:* Entire network crashes if the central coaxial backbone breaks. Heavy collisions.
*   **Star:**
    *   *Pros:* Highly robust; if one cable breaks, only that single PC drops. Excellent for unguided media and modern Ethernet.
    *   *Cons:* A complete central point of failure (if the main switch dies, everything dies). Requires intensive cabling.
*   **Ring:**
    *   *Pros:* Token passing naturally prevents all data collisions. Fair access for all nodes.
    *   *Cons:* Physically breaking the closed ring cable immediately halts all communication.
*   **Mesh:**
    *   *Pros:* Highly reliable and vastly fault-tolerant (no single point of failure).
    *   *Cons:* Exceptionally high completely wiring cost and rigid physical complexity ($n(n-1)/2$ links required).

---

### Q.1(c) & Q.1(d): Collision/Broadcast Domain, Switch vs Router, Short Notes

*(Already extensively covered. Refer to 2021 Q.1c, 2021 Q.1d).*

---

### Q.2(a): Describe the layers of TCP/IP reference model with their respective functionalities. Why is TCP/IP more popular than OSI reference model?

**Layers of the TCP/IP Reference Model:**
Unlike the 7-layer OSI model, traditional TCP/IP uses 4 practical layers (or 5 including physical hardware):
1.  **Application Layer:** Contains all higher-level protocols (HTTP, FTP, DNS, SMTP). Defines how host applications interact with the network.
2.  **Transport Layer:** Facilitates reliable, sequenced end-to-end data delivery between applications. Governed strictly by TCP (reliable/connection-oriented) and UDP (unreliable/connectionless).
3.  **Internet Layer (Network):** Governed primarily by the IP protocol. Responsible for logically routing distinct, independent packets (datagrams) across vastly different network topologies to their final destination IP address.
4.  **Network Access Layer (Link):** Specifies how data mathematically forms frames and is physically pushed across the actual hardware wires linking to the local router (combining OSI Physical and Data Link layers).

**Why TCP/IP is more popular than OSI:**
*   **Implementation over Theory:** TCP/IP was explicitly built by the DoD organically alongside actual functioning networks. The protocols were written and tested *before* the model was formalized. OSI was a theoretical, rigid academic model heavily developed by committees *before* any working protocols existed.
*   **Simplicity:** OSI is highly complex with 7 layers (Session and Presentation layers are rarely used independently in reality). TCP/IP’s condensed 4-layer architecture mapped perfectly to how internet software is actually programmed in C (Applications simply opening Transport Sockets).
*   **Free Standard:** The TCP/IP protocol suite was baked freely into Berkeley UNIX, driving massive ubiquitous adoption, while OSI protocols were heavily bureaucratic and proprietary.

---

### Q.2(b): What do you mean by framing? Describe character count and bit stuffing methods of framing with their advantages and disadvantages.

**Framing:**
Framing is the exact Layer-2 (Data Link) process of breaking a raw, infinite stream of physical layer bits into discrete, decipherable, logical units of data called "frames" so the receiver can mathematically detect where a message starts and ends.

**Methods of Framing:**
1.  **Character Count:**
    *   *Mechanism:* The sender explicitly writes the total number of characters in the frame directly into a fixed-size header field. The receiver reads this integer and counts that exact number of bytes mathematically to find the end.
    *   *Advantage:* Extremely simple to implement. 
    *   *Disadvantage:* Catastrophically brittle. If a transmission error flips a single bit strictly inside the "Count" header field, the receiver loses synchronization completely and will read all subsequent frames completely incorrectly without any way to mathematically recover.
2.  **Bit Stuffing:**
    *   *Mechanism:* Each frame strictly begins and ends with a unique raw bit pattern flag (specifically `01111110`). If the source data payload maliciously happens to contain five consecutive `1`s naturally, the sender hardware aggressively "stuffs" a fake `0` bit directly after the 5th `1` to shatter the flag pattern. The receiver hardware actively "destuffs" (deletes) the `0` bit whenever it mathematically sees 5 `1`s followed by a `0`.
    *   *Advantage:* Resolves the fatal resynchronization flaw of character counting. It is highly robust because it mathematically guarantees the flag pattern is physically unique on the wire.
    *   *Disadvantage:* Requires dedicated, high-speed bit-level hardware processing circuits. It dynamically inflates the actual physical length of the transmitted frame depending purely on the mathematical payload contents.

---

### Q.2(c): Describe the TCP 3-way handshaking and TCP congestion control scheme in brief.

*(Fully detailed in 2021 Q.3a and 2022 Q.3a. Uses SYN -> SYN/ACK -> ACK. Congestion scheme strictly utilizes Slow Start and AIMD modifying a cwnd variable).*

---

### Q.2(d): Describe the checksum algorithm for error detection. Use that algorithm for calculating the check-summed frame that is to be transmitted for the frame 101100101. Consider the generator $x^3 + x^2 + 1$. Use CRC algorithm for error detection.

**Checksum Algorithm Principles (Cyclic Redundancy Check - CRC):**
CRC utilizes strict polynomial modulo-2 arithmetic to append a powerful mathematical remainder to a frame, creating a thoroughly robust error detection mechanism.
1. Given a Data frame $M(x)$ of length $m$ bits, and a Generator Polynomial $G(x)$ of length $r+1$ bits (degree $r$).
2. The sender violently appends strictly $r$ zero-bits firmly to the right side of the data frame, resulting in an extended frame computationally represented as $x^r \cdot M(x)$.
3. The sender explicitly performs modulo-2 polynomial division (using XOR exclusively for subtraction) of the extended frame exactly by the Generator string $G(x)$.
4. The remaining division remainder (which is exactly $r$ bits long) is the actual unique CRC Checksum.
5. The final physically transmitted frame dynamically replaces the previously appended zeros perfectly with the newly calculated CRC remainder.

**Calculation:**
*   **Data (M):** `101100101`
*   **Generator $(G(x) = x^3 + x^2 + 1)$:** Degree $r = 3$. The binary string represents $1\cdot x^3 + 1\cdot x^2 + 0\cdot x^1 + 1\cdot x^0 ightarrow \mathbf{1101}$.
*   Append $r=3$ zeros to Data: `101100101000`

**Modulo-2 Division:**
```text
           111101100  (Quotient)
     ________________
1101 | 101100101000
       1101
       ----
        1100
        1101
        ----
          0110
          0000
          ----
           1101
           1101
           ----
             0001
             0000
             ----
               0010
               0000
               ----
                 0100
                 0000
                 ----
                  1000
                  1101
                  ----
                   101 (Remainder / CRC)
```
*   **Result:** The mathematically calculated CRC remainder is `101`.
*   **Transmitted Checksummed Frame:** `101100101` + `101` = **`101100101101`**.

---

### Q.3(a) & Q.3(b): Segment, Packet, Frame. Port/Socket. Sliding Window.

*   **Segment vs. Packet vs. Frame:**
    *   **Segment:** The payload strictly constructed at Layer 4 (Transport, TCP). Does not use IP headers.
    *   **Packet (Datagram):** Built strictly at Layer 3 (Network, IP). It encapsulates the TCP segment by adding Source and Destination IP Addresses. 
    *   **Frame:** Built strictly at Layer 2 (Data Link). It rigidly encapsulates the IP Datagram by adding physical MAC addresses and a CRC error-correction trailer.
*   **Port vs. Socket:**
    *   **Port:** A 16-bit software construct strictly identifying a specific application process running inside a host computer (e.g., HTTP uses Port 80).
    *   **Socket:** The exact combination of an IP address physically paired with a Port number (e.g., `192.168.1.1:80`). It represents a definitive mathematical endpoint of a two-way communication link.
*   **Sliding Window:** *(Detailed in 2021 Q.2c).*

---

### Q.3(c): How Hamming code can be used for error correction? Find the Hamming code for the word "CSE". Consider ASCII codes: C: 01000011, S: 01010011, E: 01000101.

**How Hamming Code is used for error correction:**
Hamming Code structurally embeds specialized mathematical redundancy parity bits at meticulously chosen power-of-two index positions (bits 1, 2, 4, 8) within the raw data block stream. Every parity bit mathematically calculates the even/odd parity for a uniquely interwoven specific subset of subsequent data bits. If a single bit is violently corrupted in physical transit, the receiver rapidly recalculates the parity tree. The unique combination of heavily failing parity checks powerfully isolates the exact numerical index of the flipped bit, allowing the receiver hardware to physically invert it back, achieving instantaneous error correction without TCP retransmission.

**Hamming calculation for "CSE":**
Uses Even Parity for a 7-bit ASCII code. 7 data bits require 4 parity bits ($p_1, p_2, p_4, p_8$). Length = 11 bits.
Format: $P_1, P_2, D_3, P_4, D_5, D_6, D_7, P_8, D_9, D_{10}, D_{11}$

**1. Letter 'C' (1 0 0 0 0 1 1):**
*   Data: $D_3=1, D_5=0, D_6=0, D_7=0, D_9=0, D_{10}=1, D_{11}=1$
*   $P_1$ checks (1,3,5,7,9,11) $ightarrow 1 \oplus 0 \oplus 0 \oplus 0 \oplus 1 = 0 ightarrow p_1 = 0$
*   $P_2$ checks (2,3,6,7,10,11) $ightarrow 1 \oplus 0 \oplus 0 \oplus 1 \oplus 1 = 1 ightarrow p_2 = 1$
*   $P_4$ checks (4,5,6,7) $ightarrow 0 \oplus 0 \oplus 0 = 0 ightarrow p_4 = 0$
*   $P_8$ checks (8,9,10,11) $ightarrow 0 \oplus 1 \oplus 1 = 0 ightarrow p_8 = 0$
*   **Hamming for 'C': `0 1 1 0 0 0 0 0 0 1 1`**

**2. Letter 'S' (1 0 1 0 0 1 1):**
*(Solved strictly in 2021 Q.2d)*
*   **Hamming for 'S': `0 0 1 1 0 1 0 0 0 1 1`**

**3. Letter 'E' (1 0 0 0 1 0 1):**
*(Solved strictly in 2023 Q.2c)*
*   **Hamming for 'E': `1 0 1 0 0 0 0 0 1 0 1`**

---

### Q.3(d): Distinguish among CSMA/CD and CSMA/CA, TP vs Fiber, Data Link vs Network, 1-persistent vs non persistent

*   **1-persistent vs. Non-persistent CSMA:**
    *   **1-persistent:** The station strictly listens to the channel. If it mathematically detects the channel is idle, it immediately transmits its frame with absolute probability 1. If the channel is violently busy, it continuously monitors it continuously until it structurally goes idle, then transmits instantly. Very aggressive, causes massive collisions if two stations wait simultaneously.
    *   **Non-persistent:** To aggressively reduce collisions, if the channel is completely busy, the station physically does *not* continually listen. It mathematically forces itself to completely sleep and wait a completely random amount of delay time before listening again. Less greedy, but increases latency.

---

### Q.4(a): What is IP addressing? Distinguish between (i) Classful and Classless (ii) Subnetting and Supernetting (iii) Subnet mask and wildcard mask

**(i) Classful vs. Classless:**
*   **Classful:** The ancient rigid architectural routing method where the 32-bit IP space was brutally divided into fixed, defined Classes (A, B, C, D) based explicitly on the first byte. The subnet mask was inherently fixed by the class and not transmitted in routing updates.
*   **Classless (CIDR):** Classless Inter-Domain Routing completely ignores strict classes. Routers route exclusively utilizing a variable-length prefix mask (e.g., `/22`). This allows highly flexible, efficient chunk allocation of IP addresses, saving millions of addresses from waste.

**(ii) Subnetting vs. Supernetting:**
*   **Subnetting:** Borrowing bits heavily from the host portion to mathematically subdivide a single massive network block into multiple drastically smaller networks to physically isolate traffic.
*   **Supernetting (Route Aggregation):** The exact inverse. Borrowing bits backwards mathematically from the network portion to combine/collapse multiple contiguous smaller network prefixes seamlessly into one massive logical super-network advertisement, heavily shrinking BGP routing tables.

**(iii) Subnet Mask vs. Wildcard Mask:**
*   **Subnet Mask:** A mathematical 32-bit filter where a continuous string of `1`s definitively specifies the exact Network portion, and `0`s specify the Host portion (e.g., `255.255.255.0`).
*   **Wildcard Mask:** Specifically used extensively by Cisco routers in defining Access Control Lists (ACLs) and OSPF statements. It is the direct binary mathematical inverse of the Subnet Mask. `0`s structurally mean "Must Match Strictly", and `1`s mean "Do Not Care" (e.g., `0.0.0.255`).

---

### Q.4(b): Consider 'CUET IT Business Incubator' has a block of IP addresses 210.210.210.0/24. We need to create as many subnets so that each subnet contains minimum of 15 usable IP addresses.

**Calculation:**
1.  **Block:** `210.210.210.0/24`. The default Class C Mask is `/24` (24 network bits, 8 host bits available).
2.  **Requirement:** We strictly require at minimum $15$ usable IP addresses dynamically per subnet. 
3.  **Host Bits Needed:** The formula for usable hosts is $(2^h - 2) \ge 15$.
    *   If $h = 4$, then $2^4 - 2 = 16 - 2 = 14$ usable hosts. (This mathematically fails).
    *   If $h = 5$, then $2^5 - 2 = 32 - 2 = 30$ usable hosts. (This succeeds).
    *   Therefore, we explicitly require exactly **$h = 5$** host bits.
4.  **Subnet Bits:** Since we firmly started with 8 completely open host bits, and firmly require 5 for hosts, we can mathematically "borrow" $8 - 5 = 3$ bits for building the subnets.
5.  **New Subnet Mask:** The original mask heavily was string `/24`. Adding 3 borrowed bits gives mathematically `/27`.
    *   Binary: `11111111.11111111.11111111.11100000`
    *   Decimal: **`255.255.255.224`**
6.  **Number of Subnets:** We intensely borrowed 3 bits, so we dynamically create $2^3 = 8$ distinct equal-sized subnets.
    *   The "Magic Number" block size is $2^5 = 32$.

**Subnet Layout Table:**

| Subnet | Network Address | First Usable IP | Last Usable IP | Broadcast Address |
| :--- | :--- | :--- | :--- | :--- |
| **0** | `210.210.210.0` | `.1` | `.30` | `.31` |
| **1** | `210.210.210.32`| `.33` | `.62` | `.63` |
| **2** | `210.210.210.64`| `.65` | `.94` | `.95` |
| **3** | `210.210.210.96`| `.97` | `.126` | `.127` |
| **4** | `210.210.210.128`|`.129` | `.158` | `.159` |
| **5** | `210.210.210.160`|`.161` | `.190` | `.191` |
| **6** | `210.210.210.192`|`.193` | `.222` | `.223` |
| **7** | `210.210.210.224`|`.225` | `.254` | `.255` |
