---
title: Counting labeled trees
---

### Prerequisites.

Only very basic enumerative combinatorics.

### Short description.

Some problems on labeled trees that does not involve much of internal structure can be reduced to the more straightforward problems on arrays. 

### General description.

Apart from other heavy methods of counting labeled structures (graphs, say) such as generating functions, there is a remarkably elementary method called Prüfer bijection.

In short, this is well-behaved combinatorial construction that establish bijection:
$$
\Big\{\text{labeled trees on $\{1,\dots,n\}$}\Big\} 
\longleftrightarrow
\Big\{\text{arrays on $\{1,\dots,n\}$ of length $n-2$}\Big\}
$$
which is build explicitly using the algorithm described well [here](https://cp-algorithms.com/graph/pruefer_code.html) as well as in many other Internet resources. Returning to the point, we reduce problem on trees to the problem on arbitrary sequences of fixed length. The rest now is just to note several useful properties, for example that every index, say $v$, occurs $\deg v-1$ times, hence, for example, no leaves occur in the sequence. One more remarkable corollary from this bijection, so-called Cayley's formula, is the fact that the number of label trees on $\{1,\dots,n\}$ is equal to $n^{n-2}$; if one proceed more carefully, the formula $T_{n,k} = k n^{n-k-1}$ for the number of labeled forests with $k$ connected components is easily derivable. 

In short, Prüfer codes gives a simple combinatorial way to control labeled trees (and forests), though mostly in terms of degrees of their vertices. 

### Example 1.

This is a bit artificial example, but it keeps everything simple and gives a clue how to solve such kind of problems.

Find the number of labeled trees on $\{1,\dots,N\}$ such that the degrees of all vertices but leaves are equal.

Consider arrays instead of trees. We know that the number of occurrences of a vertex $v$ is equal to $(\deg v - 1)$. So, in the array which encodes the proper tree we have the equal number of occurrences of each number. So, the combinatorial task now is rather easy:
- choose $d$ numbers (where $d$ divides $n-2$) from $\{1,\dots,n\}$ which will occur in the array.
- find the number to put the selected numbers them into $(n-2)$ cells, using multinomial coefficients. 

### Online Judges
1. [Functional Graph Distribution](https://cses.fi/problemset/task/2415/) 
2. [Sasha and Interesting Fact from Graph Theory](https://codeforces.com/contest/1109/problem/D)
3. [Tree Sum](https://codeforces.com/contest/1762/problem/E)
4. [Clues](https://codeforces.com/contest/156/problem/D?locale=en)
