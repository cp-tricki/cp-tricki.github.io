---
title: One can use determinants to count lattice paths
---

### Short description

Occasionally we can encounter the combinatorial nature of determinant in other kind of problems and exploit it writing down this underlying determinant and simplifying it mathematically (or evaluating it straightforwardly when possible).

### Long description - 1

A lot of interesting mathematics hides behind the aforementioned phenomenon will be omitted here, but we shall elaborate more on practical point.

First of all, of course, comes so-called [Lindström-Gessel-Viennot lemma](https://codeforces.com/blog/entry/108395). The detailed treatment is given by the link, so we just roughly describe the idea here.

Let $G$ be a oriented acyclic graph with two sets of marked vertices $A=(A_1,\dots,A_n)$ and $B=(B_1,\dots,B_n)$. Then, consider a matrix $M$ such that $M_{i,j}$ is the number of paths between $A_i$ and $B_j$. Computing its determinant,

\[
\det M = \sum_{\pi} sign(\pi) M_{1\pi_1} \dots M_{n\pi_n}
\]

one obtains an interesting combinatorial interpretation because the product is the number of paths systems $\{A_i\to B_{\pi_i}\}$ for some permutation $\pi$, so one obtains

\[
	\det M = \sum_{\text{paths systems}(\pi)} sign(\pi).
\]

Now we can split the sum into two key summands and, as always, expect that the main part will remain, while the "correlation" part vanishes:

\[
	\det M = \sum_{\text{non-intersc}(\pi)} sign(\pi) + \sum_{\text{intersc}(\pi)} sign(\pi).
\]

Indeed, one can build an involution on the set of the intersecting paths systems, which changes the sign of the underlying permutation. That leads, of course, to the vanishing of the second summand, hence, we obtain the so-called unweighted LGV lemma:

\[
	\det M = \sum_{\text{non-intersc}(\pi)} sign(\pi).
\]

In practice, it usually turns out that the only non-intersecting paths system is that, which corresponds to the identity permutation.

### Example 1.

Some of examples can be found in the mentioned reference to LGV.

### Example 2. 

Actually, to apply this trick one have to always remember the proof of LGV, because this strategy is applicable in a number of similar situations, where we can exploit the cancellative nature of determinant.

For example, let's describe the similar trick to derive the [hook-length formula](https://en.wikipedia.org/wiki/Hook_length_formula). One can represent Young diagram $\lambda= (\lambda_1,\dots,\lambda_k)$ as the point on real line using the classical Russian construction, and adding cells as the process on those ball, more precisely, one ball jumps over another one. Then, the problem of finding the dimension (the number of standard Young tableaux) of $\lambda$ reduces to the solving the following problem:

The cells $0, 1, \dots, k-1$ contain balls, exactly one in each. We can move one ball by one further, if the next cell is empty. How many ways to reach $l_1, \dots, l_k$, where these numbers are determined by $\lambda$. 

The solution to this problem uses the very similar strategy to the the Lindström-Gessel-Viennot. We, first, find the total number of such "path systems" (ball processes) with no restriction of non-emptiness. Then, for "intersecting path systems" (bad ball processes) we can swap two balls at the time they are in the same cell and make similar calculations. Then we generalise the situation to the arbitrary number of balls, obtaining the determinantal formula for the dimension (number of standard Young tableaux). Then, we just make some algebra and obtain the desired hook-length formula. 

### Online Judges

Again, look up in the blog. 
