## Year 2022 Model Answers

### SECTION A

### Q.1(a): Briefly write out the advantages of connecting computers into a LAN and WAN.

**Advantages of a Local Area Network (LAN):**
*   **Resource Sharing:** Workstations can seamlessly share peripheral devices like printers via the network. This is significantly cheaper than buying a printer for every individual workstation.
*   **Hardware Reduction:** Workstations do not necessarily need their own huge hard disk or CD-ROM drives, which makes them cheaper to buy than independent stand-alone PCs.
*   **Centralized Storage:** Users can save their work centrally on the network file server, allowing for easier system-wide backups.
*   **Communication:** Users can communicate with each other and transfer data between workstations very easily.
*   **High Performance:** LANs provide very high network speeds and data transfer rates compared to wide area circuits.

**Advantages of a Wide Area Network (WAN):**
*   **Geographic Reach:** Covers a large geographic scope. Allows organizations to share information and files over a much larger geographical area (state, province, country).
*   **Rapid Communication:** Messages can be sent very quickly to anyone else on the extended network regardless of distance.
*   **Interconnectivity:** WANs successfully connect multiple smaller remote networks, integrating diverse local area networks (LANs) and Metro Area Networks (MANs) into a unified enterprise network structure.

---

### Q.1(b): Explain the modes of data transmission. Write out the differences among Simplex, half duplex, and full duplex communication mode.

**Modes of Data Transmission:**
Data transmission modes describe the direction of signal flow between two linked devices.

**Differences among the Modes:**

| Feature | Simplex | Half-Duplex | Full-Duplex |
| :--- | :--- | :--- | :--- |
| **Direction of Flow** | Unidirectional (one-way only). | Bidirectional, but only **one direction at a time**. | Bidirectional **at the same time** simultaneously. |
| **Channel Usage** | Dedicated fully to the sender transmitting to the receiver. | The single communication channel is shared by both, taking turns to transmit. | The communication channel is used in both directions concurrently (often via two separate wires or frequency bands). |
| **Performance** | Lowest throughput. | Moderate throughput (wait times during turn-around). | Highest throughput (no waiting). |
| **Examples** | Radio broadcast, Television broadcasting, Keyboard to CPU. | Walkie-talkie communication. | Telephone line conversations, modern Ethernet switches (100BASE-T full duplex). |

---

### Q.1(c): Give definitions of Intranet and Extranet. Differentiate between them.

**Definitions:**
*   **Intranet:** An intranet is a private computer network that is contained purely within an enterprise. It may consist of many interlinked local area networks used securely by internal employees.
*   **Extranet:** An extranet is a computer network that allows controlled access from the outside, for specific business or educational purposes. It is an extension of an organization's intranet extended to isolated users outside the organization.

**Differences:**

| Feature | Intranet | Extranet |
| :--- | :--- | :--- |
| **Primary Audience** | Strictly internal employees and staff of the organization. | Trusted external parties (partners, vendors, suppliers, and customers). |
| **Access Boundaries** | Contained entirely within the enterprise firewalls. | Permits secure, isolated access penetrating the corporate perimeter from the public internet (often utilizing VPNs). |
| **Purpose** | Internal collaboration, HR portals, corporate data sharing. | Supply chain management, B2B procurement, joint ventures. |
| **Security Mechanism** | Relies on internal physical network security and login domains. | Heavily relies on access VPNs, tunneling (L2F, PPTP), and strict authentication to establish trust. |

---

### Q.2(a): Briefly define physical and logical topology. Write out the advantages and disadvantages of Bus, Ring, and Star topology.

**Definitions:**
*   **Physical Topology:** Refers to the physical layout and actual geometric arrangement of nodes, cables, and switches in a network.
*   **Logical Topology:** Refers to how data actually flows and is transmitted through the network from one device to the next, regardless of the physical layout (e.g., passing a token logically in a ring over a physical star wiring).

**Advantages and Disadvantages of Topologies:**

*   **Bus Topology:**
    *   **Advantages:** Simple layout. Easy to connect a computer or peripheral to a linear bus. Requires less cable length than a star topology.
    *   **Disadvantages:** Entire network shuts down if there is a break in the main backbone cable. Terminators are required at both ends. Difficult to identify the problem if the entire network goes down.
*   **Ring Topology:**
    *   **Advantages:** Every node gets equal access to the token (predictable delay). Performs better than a bus topology under a heavy network load.
    *   **Disadvantages:** A break in the closed ring cable or the failure of a single node can bring down the entire network (unless special dual-ring bypass hardware is used). Difficult to add or remove nodes without disrupting the active ring.
*   **Star Topology:**
    *   **Advantages:** High speed data transfer; particularly when the star coupler acts as a switch. Easiest to maintain and troubleshoot. Very flexible. A failure of one node or link does not affect the rest of the network.
    *   **Disadvantages:** Complete dependency on the central node/coupler; if it fails, the entire network drops. Cabling costs are higher because the number of links is strictly proportional to `n` (every node needs an independent cable).

---

### Q.2(b): How does WAN differ from LAN?

| Feature | LAN (Local Area Network) | WAN (Wide Area Network) |
| :--- | :--- | :--- |
| **Geographical Area** | Restricted to a limited geographical coverage such as a house, single office building, or school campus. | Spans a large geographic area, such as a state, province, or country. |
| **Data Transmission Cost** | Much lower, since the data transmission medium is usually owned outright by the user organization. | Very high, because the transmission mediums used are leased lines or public carrier systems (telephone lines, microwaves, satellites). |
| **Physical Connection**| Computers, terminals, and peripheral devices are typically physically connected with distinct cabling (Ethernet/fiber). | There may not be a direct hardware physical connection between the various endpoint computers. |
| **Network Speed** | Much higher than WAN. The maximum speed of a typical LAN easily reaches 1000 Megabits per second (Gbps). | Slower than LAN due to lower bandwidth availability. Speeds often max out around 150 Mbps externally. |
| **Transmission Errors**| Fewer data transmission errors due to controlled short-distance mediums. | Higher error rates due to complex routing over vast distances and varied providers. |

---

### Q.2(c): Find the differences between centralized network and distributed network.

| Feature | Centralized Network | Distributed Network |
| :--- | :--- | :--- |
| **Structure** | A type of network where all users directly connect to a singular central server. | A computer network that is structurally spread over various different networks acting jointly or separately. |
| **Role of Server** | The central server acts as the absolute agent for *all* communications. It uniquely stores both communication records and all user account info. | Functionality and resources are physically decentralized. Multiple nodes/servers operate cooperatively across the network. |
| **Processing** | All heavy processing and computations are executed exclusively on the central machine. | Besides shared communication, a distributed network often actively distributes *processing power* across participating nodes. |
| **Single Point of Failure** | Highly vulnerable. If the central database/server falls, all users are affected and the network halts. | Highly robust. There is no single point of failure. If one machine fails, the network and cached data can reroute to others. |
| **Scalability** | Generally does not scale well gracefully beyond its hardware limits. | Scales easily by adding more nodes/servers dynamically to the distributed pool. |

---

### Q.3(a): What is TCP? Explain TCP 3-way handshake process.

**TCP (Transmission Control Protocol):**
TCP is the primary transport level protocol of the Internet Protocol Suite that provides reliable, byte-oriented stream management. It offers a connection-oriented service where applications interact with TCP to send and receive data reliably across an IP network with sequencing and flow control.

**TCP 3-Way Handshake Process (Connection Establishment):**
The reliable handshake ensures both communication entities establish parameters before sending data.
1.  **SYN (Step 1):** The Active Participant (Client) sends a segment with the SYN (Synchronize) flag set to request a connection to the Passive Participant (Server). It includes the client's initial Sequence number `X`.
2.  **SYN-ACK (Step 2):** The Server receives the SYN, allocates data structures, and replies with a segment that has *both* the SYN flag and ACK flag set. The Server provides its own initial Sequence number `Y`, and acknowledges the client's sequence by setting the Acknowledgment number to `X + 1`.
3.  **ACK (Step 3):** The Client receives the SYN-ACK, and sends a final segment with just the ACK flag set, acknowledging the server's sequence by setting the Acknowledgment number to `Y + 1`.

*(See diagram in the final document: TCP 3-Way Handshake)*

---

### Q.3(b): "An IP address specifies a destination address" Explain the term.

**Explanation of the Term:**
In connectionless network systems like the Internet Protocol (IP), communication is analogous to the postal system. Each packet of data (datagram) is treated as an individual, independent entity traversing the network.
*   **The Identifier:** To ensure successful delivery, each datagram header strictly carries an "IP Address" functioning as the precise destination address to identify the intended recipient host.
*   **Format:** The IPv4 address is a 32-bit (4-byte) numerical identifier, typically represented in dotted-decimal format (e.g., `192.168.1.10`).
*   **Addressing Datagrams:** Routers across the internet rely completely on this destination address embedded within the packet header. The routing algorithm decides where the packet goes next (the output line) solely by examining this 32-bit identifier against its routing tables.

---

### Q.4(a): With regard to IP protocol, explain what is Subnetting?

**Subnetting:**
*   **Definition:** Subnetting is the defined mathematical process of strategically dividing a single larger IP network into smaller sub-divisions called subnets.
*   **Mechanism:** Computers belonging to a sub-network share a common group of most-significant bits. Subnetting breaks the IP address logically into two parts: the network routing prefix and the rest field (host identifier). 
*   **Bit Borrowing:** To create these sub-divisions, host ID bits (specifically from the bits normally dedicated to identifying hosts within a single network ID) are "borrowed" to be used as a new localized Subnet ID. 
*   Separating the main network portion and the new subnet portion of an IP address is done by performing a bitwise AND operation between the IP address and the configured Subnet Mask.

---

### Q.4(b): Discuss the idea behind Super-netting.

**Idea behind Super-netting:**
*   **The Problem:** The rapid expansion of network hosts threatened to massively inflate the size of core internet routing tables, making routing inefficient. Furthermore, the rigid classes (like Class C arrays handling max 254 hosts) were limiting for mid-size companies.
*   **The Solution (Supernetting):** Also called "route aggregation" or "route summarization," supernetting is the process of combining several independent smaller IP networks (typically consecutive Class C addresses) that share a common Classless Inter-Domain Routing (CIDR) network prefix into one large logical supernetwork.
*   **Mechanism:** It operates inversely to subnetting. Bits from the network ID are "borrowed" backwards to be used as the host ID. 
*   **Result:** By combining subnets (e.g., combining `192.60.2.0/24` and `192.60.3.0/24` into a single `192.60.2.0/23`), a single summarized address can represent several small networks. This significantly reduces the number of individual entries that must be included in global routing tables, vastly simplifying and accelerating the routing process.
