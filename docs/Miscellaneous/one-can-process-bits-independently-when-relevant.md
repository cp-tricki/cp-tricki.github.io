---
title: One can process bits independently when relevant
---

### Short description

If the problem is related with some bitwise operations (especially xor), try to think and process each bit independently.

### Prerequisites

The knowledge of bitmasks (bitwise operations)

### General description

Each integer \(x\) can be represented as \(\sum\limits_{k=0}^{M} 2^k \cdot b_k\) where \(b_k\) is \(k\)-th bit in binary representation of the integer and \(M\) is \(\log_{2}{x}\).

It is often difficult to follow all bits simultaneously, however, we can transform the expression in such way, that bits are calculated independently.

### Example

The task is to calculate \(\sum\limits_{l=1}^{n}\sum\limits_{r=l}^{n} (a_l \oplus \dots \oplus a_r)\)

**Explanations**

Let's use the trick so the expression will take form

\[
\sum\limits_{l=1}^{n}\sum\limits_{r=l}^{n} (a_l \oplus \dots \oplus a_r)=
\]

\[
\sum\limits_{l=1}^{n}\sum\limits_{r=l}^{n} (\sum\limits_{k=0}^{M} (2^k \cdot b_{l,k}) \oplus \dots \oplus \sum\limits_{k=0}^{M} (2^k \cdot b_{r,k}))\overset{*}{=} 
\]

\[
\sum\limits_{l=1}^{n}\sum\limits_{r=l}^{n}\sum\limits_{k=0}^{M} 2^k\cdot (b_{l,k} \oplus \dots \oplus b_{r,k})=
\]

\[
\sum\limits_{k=0}^{M}2^k\cdot \sum\limits_{l=1}^{n}\sum\limits_{r=l}^{n}  (b_{l,k} \oplus \dots \oplus b_{r,k}),
\]

where \(b_{i,k}\) is the \(k\)-th bit of \(a_i\) and it is equal to \(0\) or \(1\).

It's correct to do (\(\ast\)) above because multiplying by \(2^k\) is equal to shifting \(k\) bits right, and \((a\ll x)\oplus (b\ll x)=(a\oplus b)\ll x\).

Actually, the expression \((b_{l,k} \oplus \dots \oplus b_{r,k})\) is also equal to \(0\) or \(1\)(number of ones on the segment is odd). Hence it is much easier to calculate this sum (equivalently the number of segments with odd sum).

### Online Judge

1. [Krosh and one more problem with xors](https://codeforces.com/gym/102964/problem/I?locale=en)
2. [Convolution XOR SUM](https://codeforces.com/gym/104333/problem/A)
3. [XOR on Segment](https://codeforces.com/contest/242/problem/E)
4. [Present](https://codeforces.com/contest/1322/problem/B?locale=en)
