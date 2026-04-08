## SECTION B

### Q.5(a): What are the two major classes of routing algorithm? What do you mean by routing and forwarding? Why do we need distance vector and link state routing protocol?

**Answer:**
**Two Major Classes of Routing Algorithms:**
The two foundational classes are **Distance Vector (DV)** routing (which utilizes fundamentally distributed Bellman-Ford calculations based exclusively on neighbor rumors, like RIP) and **Link State (LS)** routing (where every node independently maps the entire global topology mathematically using Dijkstra's algorithm, like OSPF).

**Routing vs. Forwarding:**
*   **Routing:** The immensely complex "control plane" process. It spans the entire globally distributed network to mathematically calculate and determine strictly the optimal end-to-end paths from a source to a specific destination. It builds the routing tables.
*   **Forwarding:** The exceptionally fast, localized "data plane" action. When a singular packet biologically arrives at a router's input port, the router does a rapid hardware lookup in its forwarding table and dynamically switches the packet instantly to the appropriate output physical port.

**Why we need Distance Vector and Link State:**
We need distinct protocols because networks scale vastly differently. **Distance Vector** is fiercely needed for exceedingly simple, small-to-medium networks because it requires minuscule memory overhead and almost zero CPU processing power. **Link State** is absolutely critical for massive enterprise/ISP networks because, despite needing high CPU/RAM to hold the topological map, it completely avoids deadly routing loops, scales infinitely better, and converges mathematically instantly upon link failures.

---

### Q.5(b) & (c): Congestion Control

**Answer:**
*(Note: Briefly summarizing the fundamental mechanisms of congestion control required by the syllabus).*
Congestion violently occurs when the total number of packets rigorously dumped into a subnet strictly exceeds the physical carrying capacity of its lines and router buffers. Performance collapses precipitously.
**Key Control Mechanisms:**
1.  **Open Loop (Preventative):** Good policies implemented initially to avoid chaos. Includes **Traffic Shaping** (Leaky Bucket/Token Bucket) which violently forces erratic, bursty host traffic to forcefully conform to a predictable mathematical rate before it is ever allowed onto the primary network.
2.  **Closed Loop (Reactive):** Dynamically responding to active distress. Includes **Choke Packets** (where overloaded routers shoot distress frames backwards, begging hosts to throttle down transmission) and intense **Load Shedding** (where overloaded routers protect themselves by aggressively tossing low-priority packets into a black hole before their queues completely overflow).

---

### Q.5(d): Define count-to-infinity problem of distance vector routing algorithm. What do you mean by static and dynamic routing?

**Answer:**
**Count-to-Infinity Problem:**
The fatal mathematical flaw in rudimentary Distance Vector routing. Because routers blindly trust "rumors" passed from immediate neighbors, if a critical link violently drops offline, routers may inadvertently misinterpret obsolete paths as viable alternative routes. They end up pointing at each other in a micro-loop, incrementally increasing the believed path cost by $+1$ helplessly into infinity before mathematically realizing the node is ultimately unreachable.

**Static vs. Dynamic Routing:**
*   **Static Routing:** Network routes are rigidly configured manually by a human administrator. It physically cannot adapt to structural changes or link breaks; if a wire is cut, the network completely fails unless manually reprogrammed. Excellent securely for utterly tiny, isolated, fixed networks.
*   **Dynamic Routing:** Routers actively speak specialized languages (RIP/OSPF/BGP) to autonomously negotiate paths. They structurally sense the living topology, share intelligence, and autonomously rebuild routing tables dynamically to logically route entirely around broken hardware links on the fly.

---

### Q.6(a): Define default route and sink tree with proper examples. Use Dijkstra's algorithm for finding the shortest path from A to F.

**Answer:**
*   **Default Route:** The packet forwarding rule (route) taking effect when no other route can be determined for a given IP destination address. All packets for destinations not established in the routing table are sent via the default route.
*   **Sink Tree:** The optimal spanning tree of mathematical shortest paths structurally rooted strictly at the destination.

**Dijkstra Algorithm Principles:**
*(Generic pathfinding protocol description)*
1. Assign Distance 0 explicitly to starting node A. Assign Distance $\infty$ permanently to all others.
2. Mark A as the initial *Active* node.
3. For the Active Node, methodically scan all adjacent unvisited neighbor nodes.
4. If (Active Node's definitive score + strictly the connecting link weight) mathematically is definitively `<` the Neighbor's current stored score, completely overwrite the Neighbor's score with this newly discovered lower value.
5. Once all neighboring edges are scanned, mark the current Active Node permanently "Visited."
6. Scan the entire global graph: strictly choose the unvisited node possessing the absolute lowest score. Make this the newly Active Node. Loop to step 3 flawlessly until node F is locked.

---

### Q.6(b): What is i) Route poisoning and split horizon? ii) Load shedding and QoS

**Answer:**
**(i) Route Poisoning & Split Horizon:**
*   **Route Poisoning:** Immediately broadcasting a freshly broken link forcefully with a strict metric of "Infinity" (e.g., metric 16 in RIP) to immediately kill the route globally, overriding all other rumors and preventing Count-to-Infinity.
*   **Split Horizon:** A mathematical rule barring a router from illegally broadcasting a learned routing metric right back exactly out the physical interface it originally learned it from, killing simple two-node ping-pong routing loops instantly.

**(ii) Load Shedding & QoS:**
*   **Load Shedding:** The "big hammer" approach. When intense congestion forces a router to overflow, it just starts throwing out packets blindly to survive. Simplest way is to drop packets randomly, but discard policy may depend on the application.
*   **QoS (Quality of Service):** Replaces blind dropping. QoS implements extremely strict parameterization algorithms allowing critical time-sensitive traffic explicit priority handling in router queues (e.g., header changes to facilitate QoS).

---

### Q.6(c) & Q.6(d): ACL and IP Datagram format

**Answer:**
**ACL (Access Control List):**
*(Detailed extensively in 2022 Q.8a)* A strict firewalling sequence embedded physically on router ports filtering IP/Ports deterministically.

**IP Datagram Format Structurally:**
Depending on the version, the structure changes:
*   **IPv4 Datagram:** Optimized 20-byte core header containing: Version (4 bits), IHL (4 bits), Type of Service (8 bits for QoS), Total Length (16 bits), properties for fragmentation (Identification, Flags, Fragment Offset), TTL, Protocol (8 bits), Header Checksum (16 bits), and Source/Destination IPs (32 bits each).
*   **IPv6 Datagram:** Fixed-length 40-byte base header. The fixed format helps speed processing. Includes: Version, Traffic Class, Flow Label, Payload Length, Next Header, Hop Limit, Source/Destination IPs (128 bits each). Unlike IPv4, no fragmentation is allowed by routers (handled exclusively by endpoints).

---

### Q.7(a) & (b): DNS Namespace and Resolver Steps (Including Local Caching Scenario)

**Answer:**
**DNS Namespace:**
The DNS namespace physically strictly resembles a massive inverted tree. The absolute root is the Root Domain (a simple dot `.`). Branched below are Top-Level Domains (TLDs like `.com`, `.edu`, `.bd`). Below them are Second-Level Domains (`google.com`, `cuet.ac.bd`). This decentralized hierarchy prevents catastrophic naming collisions completely across the entire planet.

**Resolver Steps (Resolving `cuet.ac.bd` from MIT):**
1.  **Local Check:** User types URL. PC asks strictly its Local MIT ISP DNS Cache. If missing, proceed.
2.  **Root Server Query:** Local DNS formally asks the Internet Root Server (`.`). The Root server mathematically knows nothing of CUET, but authoritatively returns the IP address belonging uniquely to the `.bd` TLD Server.
3.  **TLD Server Query:** Local DNS asks the `.bd` TLD Server. It uniquely returns the structural IP belonging to the `.ac.bd` generic registry.
4.  **Authoritative Server Query:** Local DNS definitively asks the `.ac.bd` registry. The registry explicitly returns the final, authoritative hardware IP explicitly mapped rigidly to `cuet.ac.bd`'s physical server.
5.  **Caching & Delivery:** Local MIT DNS physically caches the result to accelerate the next immediate request globally and firmly returns it to the host PC application.

---

### Q.7(c): Write short notes on i) SSH ii) FTP iii) SMTP iv) WWW v) HTTPs

**Answer:**
**(i) SSH (Secure Shell):** A cryptographic network protocol meticulously crafted to strictly operate network services securely across unsecure networks. It comprehensively replaces the ancient plaintext Telnet protocol port 22, enabling secure remote terminal command-line access via robust public-key cryptography.

**(ii) FTP (File Transfer Protocol):** Port 20/21 application layer standard explicitly moving bulk file assets between host and server. Unencrypted traditionally, requiring intense active and passive connection management.

**(iii) SMTP (Simple Mail Transfer Protocol):** Port 25 absolute backbone protocol used definitively to push/transmit outgoing electronic mail exclusively. It cannot fetch mail; it only sends.

**(iv) WWW (World Wide Web):** An immense global informational paradigm logically constructed physically over the internet infrastructure, where massive arrays of interconnected hyperlinked HTML documents are fiercely identified systematically by Universal Resource Locators (URLs).

**(v) HTTPs (HTTP Secure):** The rigorously encrypted extension of elementary HTTP. Mapped explicitly to port 443, it encases ordinary plaintext web traffic physically within impenetrable TLS/SSL cryptographic tunnels, absolutely validating server identity via Certificates to intercept Man-in-the-Middle attacks.

---

### Q.8(a) & Q.8(b): Cryptography, Cipher, RSA Algorithm

**Answer:**
*(Cryptography deeply covered in 2023 Q.7b. RSA explicitly shown in 2023 Q.7c).*
RSA fundamentally relies explicitly on incredibly massive asymmetric prime factoring (using a uniquely mathematically linked Public and Private key suite). You encrypt freely strictly using the Public key $(C=M^e \pmod n)$ but decrypt identically solely utilizing the heavily mathematically sequestered Private key $(M=C^d \pmod n)$.

---

### Q.8(c): A key of transposition cipher is "DICTIONARY" and the plaintext is "happiness is temporary". Find the encrypted text.

**Answer:**
**Transposition Cipher Mechanism:**
1.  **Remove spaces** from the plaintext: `happinessistemporary` (20 characters).
2.  **Write the text out in columns** securely under the given key word. The key `DICTIONARY` has exactly 10 letters extensively dictating 10 robust columns.
    Since length is 20, we will mathematically perfectly have 2 full rows.

**Key:**        **`D I C T I O N A R Y`**
Index (1-10): `1 2 3 4 5 6 7 8 9 10`

**Row 1:**      `h a p p i n e s s i`
**Row 2:**      `s t e m p o r a r y`

3.  **Read out the distinct cipher text** strictly ordered alphabetically by the specific letters embedded in the key.
    Alphabetical order of `DICTIONARY`:
    `A` (Pos 8), `C` (Pos 3), `D` (Pos 1), `I_1` (Pos 2), `I_2` (Pos 5), `N` (Pos 7), `O` (Pos 6), `R` (Pos 9), `T` (Pos 4), `Y` (Pos 10).

    Let's extract the dynamic columns carefully based critically on this strict order:
*   Pos 8 (`A`): `sa`
*   Pos 3 (`C`): `pe`
*   Pos 1 (`D`): `hs`
*   Pos 2 (`I_1`): `at`
*   Pos 5 (`I_2`): `ip`
*   Pos 7 (`N`): `er`
*   Pos 6 (`O`): `no`
*   Pos 9 (`R`): `sr`
*   Pos 4 (`T`): `pm`
*   Pos 10 (`Y`): `iy`

4.  **Final Encrypted Text stringing them together:**
    **`SAPEHSATIPERNOSRPMIY`**
