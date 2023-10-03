---
title: How to use ternary search
---

### Short description

In practice, functions which first decrease and then increase (or vice versa) occur frequently. Then, one can use ternary search to find the optimal value. 

### Prerequisites 

Perhaps basic familiarity with binary search would be useful.

### Long description

**General idea.** There are a lot of unimodal functions (these are functions which first increase and then decrease or vice versa) especially of the **geometrical** flavour. In that case, one can use [ternary search](https://cp-algorithms.com/num_methods/ternary_search.html) in order to find the extremum. One can think about the suitable functions in the following way: if the argument of our function is very large (or very small) then the value is bad, because "it's far". And when we move our argument closer to the optimal one, the value constantly improves. For most functions it is more or less easy to prove rigorously after some technical efforts.

**Speed up.** If one know the general scheme of ternary search algorithm, they won't be surprised that we can choose arbitrary points to proceed, now just at the thirds. For instance, the segment ratio like $\varphi : 1 : \varphi$ or $1 : \varphi : 1$, where $\varphi = (1+\sqrt{5})/2$ would be a better choice if we apply memoization to long-working cost (or penalty) function we optimise. 

**Multidimensional ternary search.** See [here](https://codeforces.com/blog/entry/98524).

What follows is a sheaf of examples. 

### Example 1

Town X is in the point $(0,1)$, and Town Y in the point is in the point $(1,0)$. There is a line $y=a$, where $0\leq a\leq 1$. Speed when $y<a$ is $v_1$ and speed when $y>a$ is $v_2$. Find the minimal time to go from Town X to Town Y. 

**Explanation.**

In any way we need to intersect the line $y=a$. Let $(x,a)$ be a point on that line in which we are going to intersect it. The time then is

\[
	f(x) = \frac{\sqrt{x^2+(a-1)^2}}{v_1} + 
	\frac{\sqrt{(x-1)^2+a^2}}{v_2} 
\]

This function is clearly unimodal, hence we can use ternary search to find the optimal $x$. The generalisation of this problem can be solved using Lagrange multipliers. 

### Example 2

There are $n$ lines in the plane. Find a point such that the sum of distances from it to these lines are minimal.

**Explanation.**

Given a fixed $x$-coordinate one easily finds the optimal $y$-coordinate $find\_opt(x)$. Then, to find an optimal $x$-coordinate one do nested ternary searches when comparing: $calc(a, find\_opt(a))$. 

### Example 3

(One can imagine towers of boxes in the following problem.) Given an array $a_1,\dots,a_n$ such that $a_k \geq 0$ for all $k$, one can perform two operations:

- choose $k$ and increase $a_k$ by one,

- choose $k$ such that $a_k\geq 1$ and decrease it by one. 

Find the minimal value of operations needed to make at least $M$ numbers in the array equal.

**Explanation.**

Let $H$ be a desired height for those "at least $M$". We can greedily calculate the number of operations needed. More or less it is clear that this function is unimodal. 

### Example 4

There are $n$ fans who live on $x$-axis in coordinates $x_1,\dots,x_n$. Also, $k$-th person has speed $v_i$ m/s and can hear if the source is not farer than $d_i$ meters from themselves. A band wants to give a concert in such an integer point that they total time people spent to reach a point when they can hear the concert is minimal.

**Explanation.**

Perform ternary search of $x$-coordinate of the concert. Then, compute how much time people need to get the nearest hearable point. 
