### SECTION B

### Q.5(a): What is routing protocol in computer network? Briefly explain the features of (i) distance vector and link state routing protocol, (ii) Intra domain and inter domain routing protocol.

**Routing Protocol:**
A routing protocol is mathematically distributed software executing on hardware routers that communicates strictly with neighboring routers to exchange network intelligence. It allows routers to autonomously discover distinct networks on the Internet and mathematically build complex routing/forwarding tables to calculate the most exceptionally optimal paths for transporting IP datagrams to their destination.

**(i) Distance Vector vs. Link State:**
*(Detailed securely in 2021 Q.5a)*
*   **Distance Vector (DV):** Bellman-Ford algorithm based. Nodes exclusively share known distance information completely blindly *only* with their immediate physically connected neighbors. Slower convergence, vulnerable heavily to count-to-infinity routing loops.
*   **Link State (LS):** Dijkstra's algorithm based. Nodes fiercely reliably flood their local physical link connectivity statuses perfectly to absolutely every other node across the entire network topology. Every router independently maps the full global graph map mathematically to compute the strict shortest path. Loop free.

**(ii) Intra-domain vs. Inter-domain:**
*   **Intra-domain (IGP):** Designed exceptionally to route packets internally strictly *within* the autonomous framework of a single Autonomous System (AS). Driven purely by performance metrics (e.g., OSPF, RIP).
*   **Inter-domain (EGP):** Designed mathematically to route packets securely *between* completely different Autonomous Systems across the global Internet backbone. Driven by policy, cost, and administrative rules (e.g., BGP v4).

---

### Q.5(b): Define default route and sink tree with appropriate examples. Use Dijkstra's algorithm for finding the shortest path from A to D for the network.

**Definitions:**
*(Defined thoroughly based on course excerpts in 2021 Q.6a)*
*   **Default Route:** The packet forwarding rule (route) taking effect explicitly when no other distinct, specific route can be determined logically for a given IP destination address. All completely obscure packets are dynamically forwarded to the default route gateway matrix.
*   **Sink Tree:** The optimal topological spanning tree of mathematical shortest paths structurally rooted rigidly at the final destination router.

**Dijkstra's Algorithm (A to D):**
*(Note: A graph is explicitly needed to completely solve this. Assuming a standard generic 5-node graph where path A-B-D is 5 and A-C-D is 6, etc. See actual exam paper for the precise node weight diagram. The fundamental steps shown in 2021 Q.6a thoroughly apply).*

---

### Q.5(c) & Q.5(d): Route poisoning, split horizon, ACL vs Firewall

*(Route poisoning & Split horizon meticulously detailed in 2021 Q.6b).*

**ACL vs. Firewall:**
*   **ACL (Access Control List):** A mathematically ordered sequence of deterministic packet-filtering rules statically configured dynamically on router interfaces. It filters specifically based on Layer 3 (IPs) and Layer 4 (Ports). It structurally is stateless, blindly examining each packet in utter isolation purely against the rule list.
*   **Firewall:** A distinct, vastly more powerful massive hardware/software security appliance (or server cluster). Firewalls natively implement ACLs, but vastly extend them securely to Layer 7 (Deep Packet Inspection). They are crucially **stateful** (dynamically tracking the state of massive, multi-step TCP application connections). They structurally protect two networks by definitively sitting explicitly between the Corporate Network Premises and the external Internet.

---

### Q.6(a), (b), (c): Congestion factors, Hop-by-Hop choke, Fragmentation

**Congestion Factors:**
1.  **Too immense traffic:** Hosts violently pumping packets heavily beyond line capacity.
2.  **Weak router CPUs:** Slow switching fabrics structurally bottlenecking queued packets.
3.  **Low memory:** Minuscule hardware buffer queues overflowing rapidly.

**Hop-by-Hop Choke Packets:**
As compared to the rudimental standard choke packet technique (which warns only the original source), the hop-by-hop choke packet algorithm heavily restricts the flow significantly more rapidly. 
*   **Mechanism:** In this strict approach, the choke packet dynamically stops and mathematically aggressively chokes *each and every intermediate router* specifically along the path exactly as it propagates backward.
*   **Advantage:** At high speeds over vast distances, waiting for the sender to slow down fails wildly. Hop-by-hop gives an immediate one-step reduction essentially instantly stabilizing the heavily congested node before cascading failures happen.

**Fragmentation:**
Because massive heterogeneous physical networks (like Ethernet vs ATM) have differing strict Maximum Transmission Units (MTU), huge IP Datagrams must be mathematically shattered.
*   **Transparent Fragmentation:** A localized edge router strictly shatters the packet tightly upon physically entering the small-MTU backbone. Specifically, the exit-edge router structurally reassembles definitively the fragments *before* passing it securely on to the wider internet.
*   **Non-transparent Fragmentation:** A router forces structural fragmentation, but the independent fragments stay utterly shattered. *Only* the final terminal destination endpoint host physically mathematically shoulders the intense burden of piecing and reassembling the whole package.

---

### Q.7(a): What do you understand by DNS Name space? Describe how a resolver looks-up the remote name? Consider a resolver on eecs.admission.mit.edu wants to know the IP address of host cuet.ac.bd.

**DNS Namespace:**
The Domain Name System structurally adopts a highly decentralized, massive inverted tree structure globally. The top is the Root Domain, recursively splitting out into TLDs (`.com`, `.edu`) and subdomains.

**Resolver Lookup Process:**
The physical Application systematically invokes the mathematical `gethostbyname()` command within the host OS system. The system's DNS Resolver immediately takes aggressive action.

**Scenario (`eecs.admission.mit.edu` resolving `cuet.ac.bd`):**
1.  **Local Server Contact:** The MIT resolver application firmly contacts its internally configured local MIT Recursive Name Server reliably.
2.  **Iterative Root Query:** The local MIT server immediately executes an Iterative Query actively directly against the Global Root DNS server. The Root returns the robust IP address of the `.bd` TLD authoritative server.
3.  **Iterative TLD Query:** The local MIT server iteratively queries the `.bd` server. The `.bd` server effectively returns the firm IP of the `.ac.bd` server.
4.  **Authoritative Query:** The local MIT server queries the `.ac.bd` authoritative server. This server dynamically completely owns `cuet`, and actively returns the ultimate binary IP address for `cuet.ac.bd`.
5.  **Return & Cache:** The local MIT DNS explicitly caches the resolved IP locally to save processing heavily on the root network later, and securely returns it firmly to the resolver sitting on `eecs`.

---

### Q.8(b): A key of the transposition cipher is "LOCKDOWN" and the plain text is "stayhomestaysafe". Find the encrypted cipher text.

**Transposition Cipher Calculation:**
1.  **Preparation:** Remove all formatting spaces. The completely stripped plaintext essentially is `stayhomestaysafe` (16 letters).
2.  **Matrix Setup:** Write out dynamically the strictly 8-letter Key.
    **Key:** `L O C K D O W N`
    Since the physical plaintext is 16 letters intimately, we mathematically perfectly fill exactly $16/8 = 2$ rows cleanly.
3.  **Rows:**
    Row 1: `s t a y h o m e`
    Row 2: `s t a y s a f e`

4.  **Dictionary Ordering:** Now uniquely alphabetize critically out the columns dynamically based precisely on the Letters in the Keyword `LOCKDOWN`.
    *   Alphabetized Key: `C`, `D`, `K`, `L`, `N`, `O_1`, `O_2` , `W`
    *   Index of original columns mathematically corresponding inherently to this perfectly sorted ordered: 
        *   `C` is column 3.
        *   `D` is column 5.
        *   `K` is column 4.
        *   `L` is column 1.
        *   `N` is column 8.
        *   `O_1` is column 2.
        *   `O_2` is column 6.
        *   `W` is column 7.

5.  **Extract Data by Columns systematically:**
    *   Col 3 (`C`): `aa`
    *   Col 5 (`D`): `hs`
    *   Col 4 (`K`): `yy`
    *   Col 1 (`L`): `ss`
    *   Col 8 (`N`): `ee`
    *   Col 2 (`O_1`): `tt`
    *   Col 6 (`O_2`): `oa`
    *   Col 7 (`W`): `mf`

6.  **Final Encrypted Array assembled:** 
    **`AAHSYYSS EETTOAMF`**
    *(Spaces purely added above strictly for mathematical reading clarity. Formally: `AAHSYYSSEETTOAMF`)*
