---
title: Permutations can be represented as graphs
---

### Short description

If the problem is about permutations, try to think about them as graphs.

### Prerequisites

No specific knowledge.

### General description

Consider a permutation $p_1,p_2,\dots, p_n$. Let's construct an undirected graph where exist an edge between $i$ $\leftrightarrow$ $p_i$. In such construction this graph will contain only cycles (isolated vertex-loop, forward-backward edges or usual cycles).
For example $[2,4,5,1,3]$ will split into $[{\textcolor{blue}{2}},{\textcolor{blue}{4}},{\textcolor{red}{5}},{\textcolor{blue}{1}},{\textcolor{red}{3}}]$.
In problems, it may be efficient to consider each cycle independently.

### Example 1

Given a permutation $a$. You can choose any two indexes $i,j$ and swap $a_i,a_j$. What is the minimal number of swaps to make the permutation sorted?

### Explanations

Let's consider a cycle of the permutation. Suppose it's length is $m$. We can make all the elements from the cycle to be on their places in $m-1$ operations. That's because if $m-1$ elements will be on their place, the $m$-th will also be on its place.

So the answer to the problem is the sum of cycle lengths minus the number of cycles. If the number of cycles is $c$ than the answer is $n-c$.

### Example 2

You need to process two types of queries:

- swap $p_x,p_y$.
- find the value of $i$ if you assign $i=p_i$  $k$ times.

### Explanations

Let $S\approx \sqrt{n}$. For each $i$ we can calculate the position of $i$ after applying $S$ times $i=p_i$. (Very similar to the technique using in tree jumping). Now, we can answer the second query in $O(\frac{k}{S}+S)$ jumping $\frac{k}{S}$ times with the step of length $S$, what is precalculated, and the remainder jumps with step of length $1$.

To perform updates, you should notice that only $2 \cdot S$ values will change ($S$ jumps forward and $S$ jumps back).

### Online judges
- [Minimum Swaps 2](https://www.hackerrank.com/challenges/minimum-swaps-2/problem)
- [Swap Round Sorting](https://cses.fi/problemset/task/1698)
- [Permutation and Queries](https://codeforces.com/problemset/problem/1619/H?locale=en)
- [Lucky Permutation](https://codeforces.com/contest/1768/problem/D?locale=en)
