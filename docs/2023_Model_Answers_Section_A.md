## Year 2023 Model Answers

### SECTION A

### Q.1(a): Differentiate between OSI and TCP/IP Reference Model. Encapsulation helps to form the layer. Justify it.

**Difference Between OSI and TCP/IP Reference Model:**

| Feature | OSI Reference Model | TCP/IP Reference Model |
| :--- | :--- | :--- |
| **Layer Count** | Defines 7 discrete layers (Application, Presentation, Session, Transport, Network, Data Link, Physical). | Defined with 4 abstraction layers (Application, Transport, Internet, Network Access). |
| **Layer Grouping** | Upper layers (Application, Presentation, Session) handle software; lower layers handle network hardware and routing. | Combines OSI layers 5, 6, 7 into a single Application layer, and layers 1, 2 into a Network Access layer. |
| **Development** | Theoretical model developed by ISO to standardize communication standards. | Practical, deployed model developed by DARPA/DoD around actual protocols (TCP and IP). |
| **Connection Service** | The Network layer supports both connectionless and connection-oriented communication. | The Internet layer exclusively supports connectionless communication (IP). |
| **Protocol Independence** | Model was defined before protocols, making it very protocol-independent. | Model is tightly coupled with its protocols; it's a description of existing protocols. |

**Justification: "Encapsulation helps to form the layer"**
*   **Definition:** Encapsulation is the process in which each OSI layer receives data from the layer above, treats it as a payload, and adds its own protocol-specific control information (a header or trailer).
*   **Forming the Layer:** The OSI layers use these various forms of control information to communicate with their peer layers in other computer systems. For example, a TCP segment at the Transport layer is encapsulated inside an IP packet at the Network layer. 
*   **Modularity:** Because each layer is abstracted and only reads/processes its own specific header, encapsulation inherently forms strict layer boundaries, ensuring that a protocol at one layer does not need to understand the protocols at another layer.

---

### Q.1(b): Write out the advantages of Unshielded Twisted Pair (UTP) over Shielded Twisted Pair (STP).

**Advantages of UTP over STP:**
*   **Cost-Effectiveness:** UTP is significantly less expensive to manufacture and purchase than STP because it lacks the internal foil or braided shielding.
*   **Installation & Flexibility:** UTP has a much smaller outer diameter and is more flexible, making it easier to install, route through tight conduits, and terminate than the bulkier STP cable.
*   **Maintenance:** UTP requires less maintenance. STP shielding must be properly grounded at both ends; if grounding is imperfect, the shield acts as an antenna, drawing in more noise than it blocks. UTP eliminates this complex grounding requirement.
*   **Adequate for Most Usage:** For most indoor, standard LAN topologies (Voice grade Cat 3, Data grade Cat 5 up to 100 Mbps), UTP provides perfectly adequate transmission without the added bulk and cost of STP, especially in Star topologies.

---

### Q.1(c): Briefly explain what will happen if you hybridize star topology with ring topology and what will be the circumstances you will face to set up? Draw the figure.

**Hybridizing Star and Ring Topologies:**
When these topologies are hybridized, the physical network is wired like a **Star** (with all nodes connecting to a central hub/coupler), but logically the data travels in a **Ring** path. The central device acts as a Multistation Access Unit (MAU) that internally bridges the transmit pair of one node to the receive pair of the next node.

**Circumstances and Challenges in Setup:**
*   **Cabling Medium:** Fiber optics or twisted pair are suitable for use in ring and star topologies. Setting this up requires running point-to-point links (one for transmit, one for receive) from every node back to the central hub.
*   **Central Point of Failure:** While the logical ring prevents packet collisions, the physical setup creates a single point of failure at the central hub. If the internal ring wiring in the MAU fails, the entire network drops.
*   **Fault Detection:** Setting up the network requires hardware that can automatically bypass a faulty node or broken cable run, allowing the ring to instantly close loop and preserve the remaining connectivity.

*(See diagram in the final document: Network Topologies)*

---

### Q.2(a): What extended Star Topology gives us that star topology didn't? What are the disadvantages of star topology?

**Extended Star Topology vs. Standard Star Topology:**
*   **Network Expansion:** In a standard star topology, each station directly connects to a single common central node (star coupler). An extended star topology connects individual star central nodes to a higher-level central node, building a hierarchical structure. 
*   **Distance/Reach:** An extended star allows the network to cover a much larger geographical area (like spanning multiple floors or buildings) by distributing hubs, whereas a standard star is limited by the maximum cable length from the single central hub.
*   **Compartmentalization:** It groups nodes logically, helping contain local traffic within local hubs without flooding the core central hub.

**Disadvantages of Star Topology:**
*   **Single Point of Failure:** The entire network depends entirely on the central node/coupler. If the central hub fails, all connected stations lose connectivity.
*   **Cable Cost (Proportional to 'n'):** Every single station must have its own dedicated physical cable span running all the way back to the central node. As the number of links (*n*) grows, wiring complexity and cabling cost increase rapidly compared to a Bus topology.

---

### Q.2(b): Can Shannon theorem be used to find the maximum bit rate for a channel? In what way SNR differs from channel bandwidth?

**Using the Shannon Theorem:**
*   Yes, the **Shannon capacity gives us the upper theoretical limit** (maximum bit rate) for a channel. It defines the theoretical max bit rate in a noisy channel where random noise is present. 
*   Formula: `C = B log₂(1 + SNR)`. Even though Shannon formula gives this upper limit, for better performance, practical transmission usually chooses a target bit rate lower than `C` and uses the Nyquist formula to find the required signal levels.

**How SNR differs from Channel Bandwidth:**
*   **Channel Bandwidth (B):** Measured in Hertz (Hz), it represents the physical frequency range that the medium can reliably transmit (e.g., 300 to 3300 Hz for a telephone line). It is a property of the physical medium.
*   **Signal-to-Noise Ratio (SNR):** Measured in Decibels (dB), it is the ratio of average signal power to average noise power (S/N). It represents the clarity or quality of the signal against background thermal noise, not the physical frequency range.

---

### Q.2(c): Explain Nyquist Bit rate. In a channel state what are the relationships between Shannon capacities & Nyquist theorem?

**Nyquist Bit Rate:**
*   **Definition:** The Nyquist theorem defines the theoretical maximum bit rate in a **noiseless (perfect)** channel. 
*   It states that even perfect channels have limited capacity. To find what data rate and signal levels are appropriate, the formula used is: `BitRate = 2 * B * log₂(L)`, where `B` is bandwidth and `L` is the number of signal levels.

**Relationship Between Shannon and Nyquist:**
*   **Shannon gives the theoretical limit (Capacity):** Shannon's theorem extends Nyquist by accounting for random noise. In any real channel, the transmission limit cannot exceed the Shannon Capacity `C = B log₂(1 + SNR)`, no matter how many signal levels `L` are used.
*   **Nyquist gives the required signaling levels:** In practice, both methods are used together. First, the Shannon capacity gives us the upper limit based on the noise. Then, the Nyquist formula tells us how many signal levels (`L`) we need to actually achieve a target data rate that is safely below the Shannon limit.

---

### Q.3(a): What is 'Bit stuffing' and 'Character stuffing'? Using appropriate diagram of frame, describe framing process.

**Bit Stuffing vs. Character Stuffing:**
*   **Framing Boundary Context:** The Data Link Layer translates the raw bit stream into discrete units called frames. To know where a frame begins and ends, unique flag sequences are used.
*   **Character Stuffing:** Used in byte-oriented protocols. A special byte (flag character) marks the boundary. If the flag character appears in the data payload, an 'escape' character is inserted (stuffed) before it to ensure it isn't misread as the end of the frame.
*   **Bit Stuffing:** Used in bit-oriented protocols (like HDLC). The frame boundary is defined by the bit sequence `01111110`. If the user data contains five consecutive `1`s, the sender's hardware automatically inserts (stuffs) a `0` immediately after them to prevent it from accidentally creating the flag sequence. The receiver detects the five `1`s and automatically removes the stuffed `0`.

**Framing Process:**
1.  **Header:** Contains control information (source/destination MAC addresses).
2.  **Payload:** The physical layer's raw bit stream (upper layer packet). Stuffing is applied here to prevent accidental flag sequences.
3.  **Trailer:** Contains Error Control (e.g., CRC) to detect single-bit or burst errors.
4.  **Flags:** Unique sequences (e.g., `01111110`) placed at the start and end of the frame.

---

### Q.3(b): "Go back N ARQ is advantageous over Stop & Wait ARQ" - Explain. In "Go Back N ARQ" what does the window size specify? Does it have any relation with propagation delay?

**Advantage of Go-Back-N over Stop-&-Wait:**
*   **Stop-and-Wait ARQ:** Very inefficient because it transmits one frame, and then stops to wait fully for the propagation delay of the frame going and the ACK coming back. If the line is long or high-bandwidth, the channel is mostly idle.
*   **Go-Back-N ARQ (Pipeline):** Allows the sender to transmit multiple frames consecutively before requiring an acknowledgment. This keeps the network pipe full and drastically increases channel utilization and overall throughput, making it highly advantageous over Stop-and-Wait.

**Window Size and Propagation Delay:**
*   **What Window Size Specifies:** The window size (`N`) specifies the maximum number of unacknowledged frames the sender is allowed to have in transit at any given time.
*   **Relation to Propagation Delay:** The window size must be mathematically related to the round-trip propagation delay. **Propagation Delay** refers to the time necessary for a single bit to travel end-to-end on a physical wire. To maximize efficiency (so the sender doesn't stall waiting for ACKs), the window size `N` must be large enough to hold all the frames that can be transmitted during the Round Trip Time (RTT), preventing the sender from ever entering an forced idle phase.

---

### Q.3(c): The polynomial arithmetic is done modulo 2. Suppose a message 1101000 is to be sent over network, calculate the data sent over network using suitable generator polynomial divisor and what technique does this specify?

**Technique Specified:**
This specifies the **Cyclic Redundancy Check (CRC)** error detection technique, utilizing polynomial arithmetic done modulo 2 (which is effectively XOR arithmetic without carries).

**Given:**
*   Message (`M`): `1101`
*   Message appended with 3 zeros for division (`k` as per lecture): `1101000`
*   Generator Polynomial / Divisor (`P`): `x³ + x + 1` which translates to binary `1011`. (Since we appended 3 zeros, the divisor must be 4 bits).

**Calculation (Modulo-2 Division):**
We divide `1101000` by `1011` using XOR:

```text
         1110  (Quotient)
     ________
1011 | 1101000
       1011
       ----
        1100
        1011
        ----
         1110
         1011
         ----
          1010
          0000
          ----
           101  (Remainder) ---> Actually, let's recalculate precisely:
```

**Precise Modulo-2 XOR Steps:**
1.  `1101` XOR `1011` = `0110`
2.  Bring down `0` -> `1100`
3.  `1100` XOR `1011` = `0111`
4.  Bring down `0` -> `1110`
5.  `1110` XOR `1011` = `0101`
6.  Bring down `0` -> `1010`
7.  `1010` XOR `1011` = `0001`
*   **Remainder (`r`):** `001`

**Final Data Sent:**
The CRC remainder `001` is appended to the original message `1101`.
The bit frame `(k+r)` actually transmitted is **`1101001`**.

---

### Q.4(a): Briefly write out the IP address classes their ranges and how does an IP address have components to determine identifiers.

**IP Address Classes and Ranges:**
Traditional IPv4 addresses are divided into classes to accommodate networks of varying sizes.
*   **Class A:** `0.0.0.0` to `127.255.255.255`. Designed for extremely large networks.
*   **Class B:** `128.0.0.0` to `191.255.255.255`. Designed for medium-sized networks.
*   **Class C:** `192.0.0.0` to `223.255.255.255`. Designed for smaller local area networks.
*   **Class D:** `224.0.0.0` to `239.255.255.255`. Reserved strictly for Multicast addressing.
*   **Class E:** `240.0.0.0` to `255.255.255.255`. Reserved for experimental/future use.

**Components to Determine Identifiers:**
An IP address is logically broken into two primary components, separated using a subnet mask or CIDR notation:
1.  **Network Prefix (Network ID):** A common group of most-significant bits used for routing datagrams to the correct specific network.
2.  **Rest Field (Host ID):** The remaining bits used to uniquely identify a specific host/node within that localized network.

---

### Q.4(b): Define "Super netting" and how differs from Subnetting.

**Subnetting:**
*   **Definition:** Subnetting is the process of dividing a single IP network into smaller, logical sub-divisions called subnets.
*   **How it works:** In subnetting, bits from the Host ID field are "borrowed" to be used as a subnet identifier. For example, breaking a `/24` network into smaller `/26` sub-networks. This isolates traffic and improves security.

**Supernetting (Route Aggregation):**
*   **Definition:** Supernetting is the process of combining several smaller IP networks into one large network with a common Classless Inter-Domain Routing (CIDR) prefix.
*   **How it works / Difference:** It is the exact inverse of subnetting. In supernetting, bits from the Network ID are "borrowed" to be used as the Host ID. For example, combining networks `192.60.2.0/24` and `192.60.3.0/24` into a single supernetwork `192.60.2.0/23`.
*   **Purpose:** Supernetting drastically reduces the number of entries in a routing table, simplifying the routing process and conserving router memory (aggregation).

---

### Q.4(c): Given block of IP addresses ranging from 172.16.0.0 to 172.16.3.255. You need to create subnets using VLSM for 50 PCs and 23 PCs respectively. State your process precisely.

**Step 1: Identify the Base Network Block**
The range `172.16.0.0` to `172.16.3.255` encompasses 1024 IP addresses.
*   Network: `172.16.0.0/22`
*   In VLSM (Variable Length Subnet Masking), we allocate the largest requirement first.

**Step 2: Allocate Subnet 1 (Requirement: 50 PCs)**
*   Address space needed: 50 hosts + 2 (Network & Broadcast address) = 52 addresses.
*   The closest power of 2 that supports this is `2⁶ = 64`. Thus, we need 6 bits for the host ID.
*   **Prefix length:** 32 - 6 = **`/26`**
*   **Subnet Mask:** `255.255.255.192`
*   **Network Address:** `172.16.0.0/26`
*   **Range:** `172.16.0.0` to `172.16.0.63`
    *   *First Usable:* `172.16.0.1`
    *   *Last Usable:* `172.16.0.62`
    *   *Broadcast:* `172.16.0.63`

**Step 3: Allocate Subnet 2 (Requirement: 23 PCs)**
*   Pick up from the next available continuous address block: `172.16.0.64`.
*   Address space needed: 23 hosts + 2 = 25 addresses.
*   The closest power of 2 that supports this is `2⁵ = 32`. Thus, we need 5 bits for the host ID.
*   **Prefix length:** 32 - 5 = **`/27`**
*   **Subnet Mask:** `255.255.255.224`
*   **Network Address:** `172.16.0.64/27`
*   **Range:** `172.16.0.64` to `172.16.0.95`
    *   *First Usable:* `172.16.0.65`
    *   *Last Usable:* `172.16.0.94`
    *   *Broadcast:* `172.16.0.95`
