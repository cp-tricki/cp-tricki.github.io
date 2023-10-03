---
title: Lagrange multipliers can simplify tricky optimisation problems
---

### Short description

One can use the method of Lagrange multipliers to get rid of convoluted constraints.

### Prerequisites

Understanding of Lagrange multipliers, binary and ternary search.

### Long description

Sometimes we encounter problems with additional natural constraints, which can arise both from (mainly) geometrical and combinatorial nature of the problems. This approach is largely similar to [linear programming duality](https://codeforces.com/blog/entry/105789), but if one has a non-linear problem and is lucky enough so it is possible to make some more or less messy computation by hand and obtain one-parameter optimisation problem, the rest is something quite standard like binary or ternary search.

### Example ([eolymp](https://www.eolymp.com/ru/problems/2692))

There is a stripped land, each strip has a height of $h_i$ (through which one goes with speed $v_i$), and the overall width of the zone is $Z$. We need split the width to zones of width $Z_1,\dots,Z_n$ (so $Z_1+\dots+Z_n=Z$) such that the total time to go through the rectangles $Z_1\times h_1, \dots, Z_n\times h_n$ is minimised. For more clarity, see the image by the link.

**Explanation.**

We have a cost function

\[
	f(Z_1,\dots,Z_n) = 
	\sum_{1\leq i\leq n} \frac{\sqrt{h_i^2 + Z_i^2}}{v_i} \longrightarrow \min
\]

with respect to the constraint $g(Z_1,\dots,Z_n)=0$, where

\[
g(Z_1,\dots,Z_n)=Z_1+\dots+Z_n-Z.
\] 

We introduce Lagrange function

\[
	L(Z_1,\dots,Z_n,Z,\lambda) =
	f(Z_1,\dots,Z_n) - \lambda (Z_1+\dots+Z_n-Z).
\]

Find derivatives and make them equal zero

\[
	\partial_{Z_i} L(Z_1,\dots,Z_n,Z,\lambda) = 
	\frac{z_i}{v_i\sqrt{h_i^2+Z_i^2}}-\lambda = 0,
\]

and after some more calculations one obtains

\[
	Z_i = \frac{\lambda v_i h_i}{\sqrt{1-\lambda^2 v_i^2}}.
\]

Put it back into constraint
\[
	g(Z_1,\dots,Z_n) = \lambda \sum_{1\leq i\leq n} \frac{v_ih_i}{\sqrt{1-\lambda^2v_i^2}}=Z.
\]

As $g$ is increasing on $(-1/v_\max,1/v_\max)$ one can find the optimal lambda using binary search and recover $Z_i$ easily as well.
