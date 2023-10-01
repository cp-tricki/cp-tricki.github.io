---
title: Small number of groups can be processed straightforwardly
---

### Short description

If the task is to say something about functions try to split them into groups with the same qualities.

### Prerequisites

Basic knowledge.

### Long description

Sometimes it may be efficient to observe how the function changes. For example, it can rapidly increase or decrease. In such cases you can divide it into groups of equal values and the total number of groups will be rather small.

Usually such functions are related with $\gcd$ or bitwise operations. 

### Example 1

Given an array $a_1,a_2,\dots a_n$. Let $F(l,r)$ is bitwise AND of the elements on the segment $[l,r]$. Count the number of different $F(l,r)$ for all pairs $1\le l \le r\le n$.

**Explanation**

Notice that $F(l,r)=F(l,r+1)$ or $F(l,r) > F(l,r+1)$ and the number of second cases is small. When the function decreases, it means that bits are removed. And the amount of bits is limited with $\log_{2}{A}$. So we can jump through the values of $F(l,r)$ which are equal and the number of such jumps will be rather small.

### Example 2

Given two arrays $c_1,c_2,\dots, c_n$ and $f_1,f_2,\dots,f_n$. At first you have $T=1$. 
You perform $n$ steps. On the $i$-th you:
- Choose $k\ge 0$ and multiply $T$ by $2^k$.
- Add $f_i\cdot \lfloor \frac{c_i}{T} \rfloor$ to the answer.
Maximize the answer.

**Explanations**

Let $ans[i][k]$ is equal to the maximal answer of the first $i$ elements where $T$ is equal to $2^k$. Notice, that we should consider $k$ only up to $\log_{2}{c_i}$, because otherwise $f_i\cdot \lfloor \frac{c_i}{T} \rfloor=0$.
The transitions are: 

\[
ans[i][k]=\max\limits_{k'=0}^{k}ans[i-1][k']+f_i\cdot \lfloor \frac{c_i}{2^k} \rfloor.
\]

### Online judges

- [Shortcuts](https://atcoder.jp/contests/abc315/tasks/abc315_f)
- [wxhtzdy ORO Tree](https://codeforces.com/contest/1878/problem/G?locale=en)
- [MEX of LCM](https://codeforces.com/contest/1834/problem/E)
- [Рудольф и коктейли](https://codeforces.com/gym/104586/problem/E) (only Russian statement available)
