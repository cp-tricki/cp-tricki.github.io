---
title: Use diagonals as parameters in grid DP problems
---

### Short description

If the problem is about paths in a grid and you've came up with non optimal dp solution, try to use the number of diagonals in dp as parameter.
### Prerequisites

Dynamical programming.

### Long description

The idea is to use the number of processed diagonals as a parameter. For example for diagonal $d=3$ we will consider cells $(3,1)$, $(2,2)$, $(1,3)$. It can be also represented as the number of moves made to reach the diagonal. When we maintain the diagonal $d$ and the column $i$, we can express the row as $j=d-i+1$ and do the transitions as usual. This trick mainly helps when you need to process more than one path which depend on the number of moves.

### Example 1

You are given a grid $A$ of size $n\times n$, and a number $A_{i,j}$ in each cell. Find two paths starting at $(1,1)$, end at $(n,n)$ such that sum of unions of these paths must is maximal.

**Explanations**

Let $ans[d][i_1][i_2]$ be the answer to the problem if we are on the $d$-th diagonal, first path ends in column $i_1$ and the second path ends in column $i_2$. The answer to the problem is $ans[2n-1][n][n]$. Since we can get the rows for both paths the transitions are obvious. Using this trick we get rid of maintaining $j_1,j_2$ and have a solution in $O(n^3)$ instead of $O(n^4)$.

### Online judges

- [Relay Race](https://codeforces.com/contest/213/problem/C?locale=en)
- [Pig and Palindromes](https://codeforces.com/contest/570/problem/E)
