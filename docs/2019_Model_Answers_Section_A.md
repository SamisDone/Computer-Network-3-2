## Year 2019 Model Answers

### SECTION A

### Q.1(a): What are the types of OSI reference model? Give a comparative analysis between OSI reference model and TCP/IP model. [12]

**Comparative Analysis: OSI vs. TCP/IP Model:**
| Feature | OSI Reference Model | TCP/IP Model |
| :--- | :--- | :--- |
| **Development** | Developed mathematically by ISO heavily as a theoretical, prescriptive model *before* protocols were invented. | Developed organically by the US DoD practically as a descriptive model *after* protocols were actively functioning. |
| **Layer Structure** | Strict 7-layer architecture (Application, Presentation, Session, Transport, Network, Data Link, Physical). | Condensed 4-layer architecture (Application, Transport, Internet, Network Access). Thoroughly merges top 3 OSI layers into one Application layer. |
| **Network Layer** | Supports heavily both Connectionless and Connection-oriented communication physically at the Network Layer. | Supports strictly Connectionless communication fundamentally at the Internet (Network) Layer (via IP). |
| **Transport Layer** | Supports exclusively Connection-oriented communication at the Transport Layer. | Supports dynamically both Connection-oriented (TCP) and Connectionless (UDP) communications. |
| **Protocol Independence**| Highly protocol-independent; it mathematically separates services, interfaces, and protocols clearly. | Not protocol-independent; closely coupled strictly with the IP protocol suite. |

---

### Q.1(b): What do you know about protocols and topologies? Write down the names of two logical topologies with their pros and cons. [11]

**Protocols & Topologies:**
*   **Protocol:** A strict set of mathematically defined rules and procedures securely governing the formatting, timing, sequencing, and error control of data exchange between completely independent devices across a network.
*   **Topology:** The structural arrangement of a network. A physical topology describes the actual physical wiring layout. A logical topology describes the conceptual path data biologically takes across the network, regardless of the physical wiring.

**Two Logical Topologies (Pros & Cons):**
1.  **Logical Ring (e.g., Token Ring passing over a physical Star):**
    *   *Pros:* Deterministic. Token passing structurally mathematically guarantees zero data collisions because only the node possessing the token can transmit. Extremely fair bandwidth allocation.
    *   *Cons:* Very slow overhead waiting continuously for the token to securely cycle, even if only one station actually wants to transmit.
2.  **Logical Bus (e.g., Ethernet CSMA/CD over a physical Hub/Star):**
    *   *Pros:* Extremely fast transmission dynamically under light loads since any node can broadcast universally at any time strictly without waiting for a token.
    *   *Cons:* Heavily nondeterministic. Collisions inherently surge structurally as network traffic load intensely increases, drastically crashing throughput efficiency.

---

### Q.1(c): What is gigabit Ethernet? How is collision handled with CSMA/CD? [12]

**Gigabit Ethernet:**
It is an advanced evolution of the IEEE 802.3 standard mathematically providing blazing raw data transfer rates of securely 1000 Megabits per second (1 Gbps), while fundamentally maintaining full backward compatibility heavily with 10 Mbps and 100 Mbps Ethernet standards and exactly identical frame formats. It predominantly runs physically over fiber optic cables or Cat5e/Cat6 twisted pair.

**How Collision is handled with CSMA/CD (Carrier Sense Multiple Access / Collision Detection):**
1.  **Listen Before Talking:** When a station wants to reliably transmit, it technically "carrier-senses" the wire to see if it is mathematically idle. If busy, it securely waits.
2.  **Transmit & Monitor:** If idle, the station eagerly begins transmission but strictly mathematically continues to actively monitor the voltage levels locally on the wire.
3.  **Detect Collision:** If the station detects a sudden, massive voltage spike physically during its own transmission, it instantly concludes a violent physical collision has firmly occurred with another station's signal.
4.  **Jam & Abort:** It aggressively immediately aborts the data transmission and intentionally sends a brief, harsh "Jam Signal" explicitly to heavily warn absolutely all other nodes that a collision has dynamically ruined the channel.
5.  **Exponential Backoff:** The station mathematically invokes the pure Binary Exponential Backoff algorithm, forcing itself aggressively to sleep for a completely random amount of microsecond time uniformly before reliably retrying the transmission securely from step 1.

---

### Q.2(a): Write down the reasons for using layered protocols. [8]

**Reasons for Layered Protocols:**
1.  **Modularity (Divide & Conquer):** It intimately breaks down the immense, monstrous complexity of global network communications firmly into much smaller, actively manageable, and well-defined mathematical sub-tasks.
2.  **Interoperability:** It strictly standardizes heavily the interfaces globally between completely different vendors, eagerly allowing hardware from Cisco to seamlessly fundamentally talk securely to hardware from Juniper.
3.  **Flexibility & Upgradeability:** A protocol completely within one specific layer can be fully replaced or modernized securely (e.g., eagerly upgrading from IPv4 to IPv6 at Layer 3) structurally without forcing any changes universally to the overlying applications (Layer 7) or underlying physical cables (Layer 1).
4.  **Troubleshooting:** Facilitates remarkably easier network fault isolation structurally by allowing engineers actively to strictly thoroughly test layers distinctly one step at a time explicitly from bottom-up or top-down.

---

### Q.2(b): Write down the names of four methods used to mark the start and end of each frame. Give appropriate examples for any two methods. [9]

**Four Framing Methods:**
1.  Character Count
2.  Character / Byte Stuffing
3.  Bit Stuffing
4.  Physical Layer Coding Violations

**Examples:**
*   **Character Count:** The sender explicitly embeds the entire integer frame length strictly into a fixed header purely at the beginning. If the frame intimately contains 5 characters, the sender physically writes `5` precisely as the very first character.
*   **Bit Stuffing:** Using a distinct flag pattern firmly (e.g., `01111110`) strictly to mark frame endpoints. If five `1`s dynamically appear universally strictly within the actual payload naturally, the sender aggressively inserts a fake `0` mathematically immediately after the 5th `1` structurally so it never uniquely matches the flag.

---

### Q.2(c): Given frame 10101011011 and generator 10001. If receiver received 10101011010, is it accurate reception? Prove by CRC. [9]

**Proof by CRC Modulo-2 Division:**
*   **Received Frame:** `10101011010`
*   **Generator (Divisor):** `10001`
*   **Rule:** If the frame securely perfectly arrived mathematically error-free, blindly dividing the entire strictly received bit string thoroughly by the generator must dynamically theoretically strictly yield a Remainder exactly equal to `0000`.

**Calculation:**
```text
           1010111    (Quotient)
      _____________
10001 | 10101011010
        10001
        -----
          10001
          10001
          -----
             001010
               0000
               ----
               1010    (Remainder)
```
Wait, let's rigidly accurately calculate Modulo-2:
1. `10101` XOR `10001` = `0100`. Pull down `0` -> `1000`. Pull down `1` -> `10001`.
2. `10001` XOR `10001` = `00000`. Pull down `1` -> `1`. Pull down `0` -> `10`. Pull down `1` -> `101`. Pull down `0` -> `1010`.
The strictly final calculated remainder is exactly `1010`.

**Conclusion:**
Since the final mathematical remainder securely is explicitly `1010` (which is uniquely **not identically zero**), this conclusively profoundly proves that errors structurally forcefully occurred purely during physical transmission dynamically. The reception intimately is **structurally NOT computationally accurate**.

---

### Q.2(d): State Shannon's theorem. A channel with S/N of 3 can transmit at a maximum rate of 4000 bps. Calculate the channel bandwidth. [9]

**Shannon's Theorem:**
Calculates heavily the absolute mathematically theoretical maximum transmission data rate strictly for a massively noisy, chaotic analog channel universally.
**Formula:** $Maximum\ Bit\ Rate\ (C) = B \cdot \log_{2}(1 + rac{S}{N})$ uniquely in bits fundamentally per dynamically second. Where $B$ is explicitly the bandwidth tightly in Hertz, and $S/N$ intricately is explicitly the raw Signal-to-Noise securely power ratio mathematically.

**Calculation:**
*   Given $C = 4000$ bps
*   Given $rac{S}{N} = 3$ (Raw numeric ratio, not dynamically Decibels)
*   Find physical $B$ uniquely.

$C = B \cdot \log_{2}(1 + rac{S}{N})$
$4000 = B \cdot \log_{2}(1 + 3)$
$4000 = B \cdot \log_{2}(4)$
$4000 = B \cdot 2$
$B = rac{4000}{2} = \mathbf{2000 	ext{ Hz}}$

**Result:** The strict channel bandwidth explicitly is **2000 Hz (or 2 kHz)**.

---

### Q.3 & Q.4: Assorted Short Concepts
*(Extensively mathematically covered inherently securely in distinctly prior thoroughly 2023, 2022, 2021 natively heavily model fundamentally answers purely.)*
