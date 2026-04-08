### SECTION B

### Q.5(a): Find the basic differences between connection-oriented and connection-less service.

| Feature | Connection-Oriented Service | Connection-Less Service |
| :--- | :--- | :--- |
| **Analogy** | Analogous to the telephone system. | Analogous to the postal system. |
| **Setup Phase** | Requires communication entities to negotiate and establish a connection (handshake) before sending any data. | No handshake required; allows entities to send data individually and directly before establishing any set communication path. |
| **Data Format** | Uses a continuous byte stream of data. | Uses discrete messages or packets (datagrams). |
| **Packet Pathing** | All packets follow the exact same established route (virtual circuit) causing them to arrive perfectly in order. | Each packet carries a destination address and can take different paths; they may arrive out of order. |
| **Robustness** | Highly vulnerable to router failure; if the circuit breaks, the connection is instantly lost. | Inherently robust to router failure; datagrams will dynamically find alternative paths. |
| **Protocols** | TCP (Transmission Control Protocol), ATM, Frame Relay. | UDP (User Datagram Protocol), IP. |

---

### Q.5(b): Distinguish differences between IPv4 and IPv6 based on the 128 bit vs 32 bit, and extension header size.

**Differences between IPv4 and IPv6:**

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Space** | Uses a highly limited 32-bit address space. | Uses a massive 128-bit address space, thoroughly solving IP allocation exhaustion. |
| **Address Hierarchy** | Standard network/host hierarchical division. | Features extensively extended address hierarchy allowing complex sub-divisions. |
| **Header Format / Size** | Header size varies (typically 20 bytes minimum) due to variable length Options fields. | Features a fixed-size, streamlined base header. The fixed header format drastically helps speed processing up at the router level. |
| **Protocol Field** | Contains a standard "Protocol" field to denote the next enclosed payload layer (like TCP). | Replaces Protocol field with a "Next Header" field. |
| **Extension Headers** | Options are crammed into the main IPv4 base header, complicating processing. | Options are handled elegantly using distinct modular "Extension headers." Extension headers are placed between the fixed IPv6 base header and the transport level header (TCP/UDP), saving base header space. |

---

### Q.6(a): Write out the functionalities of Address Resolution Protocol (ARP).

**Functionalities of ARP:**
*   **The Problem:** The network layer routing mechanism utilizes logical 32-bit IP Addresses. However, when a packet arrives at the local network segment, the physical Link Layer hardware only understands 48-bit physical MAC addresses.
*   **The Resolution:** Address Resolution Protocol (ARP) precisely bridges this gap. It provides the essential function of dynamically mapping a known logical IP address onto an unknown physical Ethernet (MAC) address.
*   **Mechanism (Broadcast Request):** If the sending system does not have the desired MAC address in its local cache, it broadcasts an ARP Request packet onto the entire Ethernet, effectively asking the network, "Who is the owner of this particular IP address?"
*   **Mechanism (Unicast Reply):** On receiving that broadcast packet, every machine checks its own configured IP address. Only the correct target machine will respond, sending an ARP Reply containing its physical MAC address directly back to the sender.

*(See diagram in the final document: ARP Process)*

---

### Q.6(b): Briefly describe what Network Address Translation (NAT) and what controversy it has? Explain with functionality and translation table format.

**What is NAT?**
Network Address Translation (NAT) is a technique deployed on routers acting as an intermediary between a private internal network and the public Internet. It allows tens of thousands of simultaneous internal connections to share a single, routable public LAN-side WAN IP address by dynamically replacing IPs and ports.

**The Controversy:**
NAT is considered "controversial" in traditional open networking because it fundamentally violates the pure end-to-end architectural principle of the Internet. According to strict TCP/IP design, every endpoint should have a unique, globally routable IP and address other endpoints directly. NAT obfuscates the true endpoints, complicating peer-to-peer protocols (like certain VoIP setups or direct file transfers), which struggle to traverse NAT firewalls since the public IP does not truly belong to the internal endpoint.

**Functionality and Translation Table:**
1.  **Outgoing:** When an internal host (e.g. `H1`) sends a datagram to the Internet, the NAT router intercepts it. It explicitly replaces the `(source IP address, original port #)` of the outgoing datagram with its own `(NAT Public IP address, newly assigned port #)`.
2.  **Tracking:** The router rigorously logs this translation pair in its internal **NAT translation table** mapping.
3.  **Incoming:** When the remote server logically responds to the `(NAT Public IP address, new port #)`, the NAT device intercepts the reply, looks up the port in its translation table, restores the original `(source IP address, original port #)`, and forwards it inwards to `H1`.

---

### Q.7(a): Discuss "flow control" and "congestion control". Why "congestion control" differs from "flow control"?

*   **Flow Control:** This is the detailed mechanism of adjusting the specific sending rate according strictly to the resources (e.g., buffer size) currently available at the final *destination* receiver.
*   **Congestion Control:** This defines algorithms and protocols that attempt to prevent or resolve the over-subscription of *network* resources (specifically links and routers) by dialing back the overall volume of packets injected into the network.

**Why Congestion Control Differs from Flow Control:**
They are frequently mixed up, but their scope of regulation is drastically different.
*   Flow control is strictly "point-to-point." It is limited in a way that it only considers what is going on exclusively between the two end devices (Sender A and Receiver B). Its sole goal is ensuring the sender does not overwhelm the receiver's memory buffers.
*   Congestion control is a "global" network issue. It regulates traffic to ensure the sender does not overwhelm the *intermediate routers and switches* forming the public network fabric.

---

### Q.7(b): What are the primary differences between virtual circuit and datagram packet switching?

**Differences in Packet Switching:**

| Feature | Virtual Circuit Packet Switching | Datagram Packet Switching |
| :--- | :--- | :--- |
| **Path Setup** | Involves a Circuit Establishment phase (connection oriented) simulating a dedicated telephone path. | Purely connectionless. No setup is required before sending packets. |
| **Addressing Overhead** | Each packet only needs to contain a short Virtual Circuit Identifier (VCI). | Each individual datagram must strictly carry full Source and Destination IP addresses. |
| **Routing Decisions** | No routing decisions are required at each node during data transfer. Routers simply look up the VCI. | Heavy routing calculation. The routing software algorithm must make independent routing decisions at each physical node for *every single datagram*. |
| **Pathing** | All packets follow the exact same pre-determined physical route edge-to-edge. | Packets handled as datagrams can dynamically take different distinct paths depending on instantaneous router congestion. |

---

### Q.8(a): Briefly write out the differences between message switching and packet switching.

**Message Switching vs. Packet Switching:**

| Feature | Message Switching | Packet Switching |
| :--- | :--- | :--- |
| **Data Formatting** | The entire message is transmitted from node to node intact as a single, large block of data. | The originating station breaks the long message structurally into smaller, fixed-size chunks called "packets". |
| **Storage & Forwarding** | Intermediate nodes must possess enough memory/disk space to temporarily store the entire massive message before forwarding it to the next hop. | Intermediate memory requirements are low (switching via fast system memory). Packets are independently buffered and swiftly forwarded one at a time to the network. |
| **Transmission Delays**| Suffers from very high latency and transmission delays since a node cannot begin sending the message to the next hop until the entire massive file is completely received. | Substantially reduces delay through pipelining. Node 2 can begin forwarding the first packet of a message while Node 1 is still transmitting the second packet. |
| **Channel Occupancy** | Dominates the shared link for an extended period, blocking other users. | Allows many pairs of nodes to interleave packets over the same shared channel simultaneously, drastically improving multiplexing efficiency. |

---

### Q.8(b): Find the disadvantages of Frame Relay & ATM. Do you consider Frame Relay as a reliable network? Mention your reason to do so.

**Disadvantages of ATM (Asynchronous Transfer Mode):**
*   The hardware cost of specialized ATM switching devices is incredibly high.
*   Because it uses tiny fixed-length packets called "cells" (typically 53 bytes), the overhead generated by the 5-byte cell header is proportionally very high compared to the payload.
*   The ATM Quality of Service (QoS) mechanism is technically quite complex to properly administer.

**Disadvantages of Frame Relay:**
*   Provides strictly unreliable service.
*   The exact order of arriving packets at the destination may not be maintained.
*   If erroneous packets are detected, they are directly dropped without notification.

**Is Frame Relay reliable?**
No, Frame Relay is specifically built to be an **unreliable** network.
**Reason:** Frame relay does not offer any built-in windowing flow control to prevent congestion. Crucially, there is no provision for the acknowledgment of received packets at the data link layer, and zero mechanism for retransmission control of corrupted frames. It implicitly assumes the underlying physical fiber lines are extremely clean (error rate of 1 bit in 10¹⁴) and pushes the entire burden of error correction end-to-end strictly to the upper transport layers (like TCP).

---

### Q.8(c): What are the differences between Exterior Gateway Protocol & Open Shortest path First?

**Differences between EGP and OSPF:**

| Feature | Exterior Gateway Protocol (EGP / BGP) | Open Shortest Path First (OSPF) |
| :--- | :--- | :--- |
| **Routing Scope** | Categorized as an Exterior Gateway Protocol. | Categorized as an Interior Gateway Protocol (IGP). |
| **Operational Boundary**| Specifically designed to route packets logically *between* entirely independent Autonomous Systems (AS's) on the global internet. | Specifically designed to route packets strictly *within* a single, localized Autonomous System using common internal metrics. |
| **Underlying Algorithm**| Usually based on generic Distance-Vector logic (Path Vector). | Uses complex Link-State routing algorithms and metrics based strictly on link costs. |
| **Supernetting Support**| Older EGP protocols do not support supernetting / CIDR aggregation directly, though its modern successor BGP does perfectly. | Fully supports CIDR and Supernetting out of the box, drastically simplifying massive internal routing tables. |
