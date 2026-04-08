# Year 2019 Self Study & Additional Questions

### Q.2(c) (Self Study): State Nyquist's theorem. A noiseless channel can transmit binary signals at a maximum rate of 8600 bps. Find out the channel bandwidth. [10]

**Answer:**
**Nyquist's Theorem:**
For a noiseless channel, the maximum bit rate is:
C = 2 × B × log₂(L)
Where C = capacity (bps), B = bandwidth (Hz), L = number of signal levels.

**Calculation:**
*   Given: C = 8600 bps, Binary signals → L = 2.
8600 = 2 × B × log₂(2)
8600 = 2 × B × 1
B = (8600)(2) = 4300  Hz)

---

### Q.4(b) (Self Study): CRC for frame `101100101` and generator `1101` (x³+x²+1).

**Answer:**
*(This is identical to year 2020 Q.2d. Already solved there.)*
*   Data: `101100101`, Generator: `1101` (degree 3).
*   Augment with 3 zeros: `101100101000`
*   After modulo-2 division, Remainder = `010`.
*   **Transmitted frame: `101100101010`**

---

### Q.4(c) (Self Study): What is Hamming distance? Find the Hamming code for the word "CUET". [12]

**Answer:**
**Hamming Distance:**
The Hamming distance between two binary strings of equal length is the number of positions where corresponding bits differ. It is found by XORing the two strings and counting the 1s.

**ASCII Codes (7-bit):**
*   C: `1000011`
*   U: `1010101`
*   E: `1000101`
*   T: `1010100`

**Hamming Code (Even Parity, 7 data bits + 4 parity bits = 11 bits):**
Format: P_1, P_2, D_3, P_4, D_5, D_6, D_7, P_8, D_9, D_(10), D_(11)

**Letter 'C' (1000011):**
*   Already calculated in 2023 Q.2c → **`01100000011`**

**Letter 'U' (1010101):**
*   Data: D_3=1, D_5=0, D_6=1, D_7=0, D_9=1, D_(10)=0, D_(11)=1
*   P_1 checks 3,5,7,9,11: 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 1 = 1 → p_1=1
*   P_2 checks 3,6,7,10,11: 1 ⊕ 1 ⊕ 0 ⊕ 0 ⊕ 1 = 1 → p_2=1
*   P_4 checks 5,6,7: 0 ⊕ 1 ⊕ 0 = 1 → p_4=1
*   P_8 checks 9,10,11: 1 ⊕ 0 ⊕ 1 = 0 → p_8=0
*   **Hamming Code for 'U': `1 1 1 1 0 1 0 0 1 0 1`**

**Letter 'E' (1000101):**
*   Already calculated in 2023 Q.2c → **`10100000101`**

**Letter 'T' (1010100):**
*   Data: D_3=1, D_5=0, D_6=1, D_7=0, D_9=1, D_(10)=0, D_(11)=0
*   P_1 checks 3,5,7,9,11: 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 0 = 0 → p_1=0
*   P_2 checks 3,6,7,10,11: 1 ⊕ 1 ⊕ 0 ⊕ 0 ⊕ 0 = 0 → p_2=0
*   P_4 checks 5,6,7: 0 ⊕ 1 ⊕ 0 = 1 → p_4=1
*   P_8 checks 9,10,11: 1 ⊕ 0 ⊕ 0 = 1 → p_8=1
*   **Hamming Code for 'T': `0 0 1 1 0 1 0 1 1 0 0`**

---

### Q.5(b) (Self Study): Consider CUET has a block 210.210.210.0/24. Subnet for 15 usable hosts. [15]

**Answer:**
*(This is identical to year 2020 Q.4b. Already solved there.)*
*   Need 15 usable hosts → 15 + 2 = 17, next power of 2 is 2⁵=32.
*   Host bits: 5. Subnet bits borrowed: 8-5=3.
*   New prefix: /27. Number of subnets: 2³ = 8.
*   Each subnet has 30 usable IPs.
*   Subnets: `.0/27`, `.32/27`, `.64/27`, `.96/27`, `.128/27`, `.160/27`, `.192/27`, `.224/27`.

---

### Q.6(b) (Self Study): Define sink tree. Use Dijkstra's algorithm from A to D. [15]

**Answer:**
**Sink Tree:**
A sink tree for a destination node is a tree formed by the union of all shortest paths from every other node in the network to that destination. It is rooted at the destination where all traffic converges ("sinks"). Every routing algorithm essentially attempts to discover and use the sink tree for each destination.

*(Dijkstra's algorithm step-by-step procedure is described in 2023 Q.6b and 2021 Q.6a. The specific numeric calculation depends on the graph provided in the figure.)*

---

### Q.8(b) (Self Study): Transposition cipher key="MEGABUCK", plaintext="pleasetransferfivelatektoinmysonalibankaccount". [10]

**Answer:**
**Transposition Cipher with Key "MEGABUCK":**
1.  **Key:** `MEGABUCK` (8 letters)
2.  **Plaintext:** `pleasetransferonemillliondollarstomyswissbankaccountsixtwotwo` 
    Wait — the given plaintext is `pleasetransferfivelatektoinmysonalibankaccount` (47 characters).
3.  **Rows:** ⌈ 47/8 ⌉ = 6 rows. 6 × 8 = 48 slots, so 1 padding char.

**Write in rows:**
```
M  E  G  A  B  U  C  K
p  l  e  a  s  e  t  r
a  n  s  f  e  r  f  i
v  e  l  a  t  e  k  t
o  i  n  m  y  s  o  n
a  l  i  b  a  n  k  a
c  c  o  u  n  t  x  x
```

4.  **Alphabetical order of key:** A=1, B=2, C=3, E=4, G=5, K=6, M=7, U=8
    *   A (col 4): `a f a m b u`
    *   B (col 5): `s e t y a n`
    *   C (col 7): `t f k o k x`
    *   E (col 2): `l n e i l c`
    *   G (col 3): `e s l n i o`
    *   K (col 8): `r i t n a x`
    *   M (col 1): `p a v o a c`
    *   U (col 6): `e r e s n t`

5.  **Cipher Text:**
    **`AFAMBUSET YANTFKOKXLNEILCESLNIO RITNAXPAVOAC ERESNT`**
    Combined: **`AFAMBUSETYANTFKOKXLNEILCESLNIORITNAXPAVOACERESNT`**

---

### Q.2(c) (CSE-411): Explain how Hamming code is used for error correction for a 4-bit data (1010).

**Answer:**
**Hamming Code for 4-bit data `1010`:**
With 4 data bits, we need r parity bits where 2^r ≥ 4 + r + 1. With r=3: 2³=8 ≥ 8. So 3 parity bits.

**Position Layout (7-bit codeword):**
P_1, P_2, D_3, P_4, D_5, D_6, D_7
Data bits: D_3=1, D_5=0, D_6=1, D_7=0

**Calculate Parity Bits (Even Parity):**
*   P_1 checks positions 1,3,5,7: P_1 ⊕ 1 ⊕ 0 ⊕ 0 = 0 → P_1 = 1
*   P_2 checks positions 2,3,6,7: P_2 ⊕ 1 ⊕ 1 ⊕ 0 = 0 → P_2 = 0
*   P_4 checks positions 4,5,6,7: P_4 ⊕ 0 ⊕ 1 ⊕ 0 = 0 → P_4 = 1

**Transmitted Codeword:** `1 0 1 1 0 1 0`

**Error Correction Example:**
Suppose bit position 5 gets flipped during transmission. Received: `1 0 1 1 1 1 0`

*   Check P_1 (positions 1,3,5,7): 1 ⊕ 1 ⊕ 1 ⊕ 0 = 1 → **Error**
*   Check P_2 (positions 2,3,6,7): 0 ⊕ 1 ⊕ 1 ⊕ 0 = 0 → OK
*   Check P_4 (positions 4,5,6,7): 1 ⊕ 1 ⊕ 1 ⊕ 0 = 1 → **Error**

Syndrome = P_4 P_2 P_1 = 101_2 = 5. Error is at position **5**. Flip bit 5: 1 → 0. Corrected codeword: `1 0 1 1 0 1 0` ✓

---

### Q.3(a) (CSE-411): Obtain the 4-bit CRC code work for the data bit sequence 10011011100 using the generator polynomial x⁴+x²+1.

**Answer:**
*   Data: `10011011100`
*   Generator: x⁴+x²+1 → Binary: `10101` (degree 4)
*   Augment data with 4 zeros: `100110111000000`

Modulo-2 Division:
```
              10000111001
         ________________
   10101 | 100110111000000
           10101
           -----
             01101
             00000
             -----
              11011
              10101
              -----
               11101
               10101
               -----
                10000
                10101
                -----
                 01010
                 00000
                 -----
                  10100
                  10101
                  -----
                   00010
                   00000
                   -----
                    00100
                    00000
                    -----
                     0100 (Remainder)
```
*   **CRC Remainder: `0100`**
*   **Transmitted Codeword: `100110111000100`**

---

### Q.3(c) (CSE-411): The bandwidth of a given channel is 1600 Hz. If the SNR is 20dB, what will be the maximum data rate of the channel in bps?

**Answer:**
**Using Shannon's Theorem:**
C = B × log₂(1 + SNR)

First, convert SNR from dB to linear:
SNR)_(dB) = 10 × log₁₀(SNR)_(linear)
20 = 10 × log₁₀(SNR)_(linear)
log₁₀(SNR)_(linear) = 2
SNR)_(linear) = 10² = 100

Now calculate capacity:
C = 1600 × log₂(1 + 100)
C = 1600 × log₂(101)
log₂(101) = (ln(101)(ln(2) = (4.615)(0.693) ≈ 6.66
C = 1600 × 6.66 ≈ 10,656  bps)
