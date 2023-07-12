---
title: How to come up with a comparator?
---

### Acknowledgements

We start from a simple trick, which was exposed by Sergei Kopeliovich at Winter Programming School in Kharkiv in 2013.

### Short description

If it seems that a problem can be solved by an algorithm of the form: "arrange the objects in a suitable way and then work greedily", there is a general strategy to devise a comparator for this sort.

### Prerequisites

No specific knowledge is required, though familiarity with greedy algorithms would be useful.

### General description

*The auxiliary problem*: find an order that optimises a construction (that is the essential part of the considered problem) if it is known that such an order exists.

We first consider a simplified problem, when only two objects exist, say \(A\) and \(B\). Then our comparator should determine which order is better: \(AB\) or \(BA\). To do so, we can normally introduce a penalty (or a cost) function \(f(A,B)\) denoting the amount of penalty (or cost) we have if one takes object \(A\) first and object \(B\) second. Then our comparator chooses that order in which the penalty is minimal (or cost is maximal). If this comparator (relation) \(A\prec B\) (which is \(A\prec B \iff penalty(A,B)<penalty(B,A)\) or \(cost(A,B)>cost(B,A)\)) is transitive (i.e. if \(A\prec B\) and \(B\prec C\) then \(A\prec C\)) then after sorting all the objects with respect to it we shall obtain the *optimal* order.

*The main problem*: find a maximal-size subset that optimises a construction. (The difference from idea 1 is that we are not forced to take *all* elements.)

To do so, we use the comparator from the *auxiliary problem*, and take objects greedily one by one. At each step, we make a choice:

1. Put this object into the answer set,

2. Replace an instance in the answer set with this object.

More generally one can write here a knapsack-like dp (if we have a subset we know the order by the auxiliary problem).

### Example 1 (a tower of boxes)

Given \(n\) boxes, each of which has its weight \(m_i\) and the weight it can carry on the top \(a_i\), determine the size of the largest tower one can build. 

**Step 1. Build a tower of all boxes.** 
In other words, we need to arrange the boxes in such a way that nothing breaks. Considering two distinct boxes, say \(i\) and \(j\), we ask: when the order \((i,j)\) is better than \((j,i)\)? Obviously, that is when the excess of our carrying abilities is greater (that is when the total weight that we can additionally carry is greater). In other words, our cost function looks like this (here box \(j\) stands on the top of \(i\)): \(f(i, j) = \min(\) total weight that can be still carried by box \(i\), total weight that can be still carried by \(j)\), i.e. \(f(i, j) = \min(a_i - m_j , a_j)\). Then we will build the tower in descending order of value.

**Step 2. Build a max-size tower.**
Sort the boxes in the increasing order with respect to the comparator from Step 1. Take them greedily: if we can put the next box below the already built tower, we do it; otherwise, we ponder whether can we replace some of the boxes in the tower with our current one and decrease the weight the bottom box carries. 

### Example 2 ([this CSES problem](https://cses.fi/problemset/task/2426)).

Given \(n\) people and their programmer skill (\(skill_1\)) and artistic skill (\(skill_2\)). We need to take exactly \(a\) programmers and \(b\) artists. Maximise total skill. 

**Step 1. Take all people, at least \(a\) programmers and at least \(b\) artists.** ([this eolymp problem](https://www.eolymp.com/en/problems/182))

Applying to this problem, the cost (answer) of order \(AB\) (take programmer skill of \(A\) and artistique skill of \(B\)) is \(skill_1(A) + skill_2(B)\), and the cost of order \(BA\) (take the artistic skill of \(B\) and programmer skill of \(A\)) is \(skill_2(A) + skill_1(B)\). Then \(cost (AB) > cost (BA)\) is equivalent to \(skill_2(A) - skill_1(A) < skill_2(B) - skill_1(A)\) which we take as our comparator.

**Step 2. Take exactly \(a\) programmers and exactly \(b\) artists.**

Below we describe our implementation of the general strategy.

**1.** (*) Take a person with the best programmer skill (we shall replace bad choices later) and keep a set X containing values of penalty function (\(skill_2(A) - skill_1(A)\), as in Step 1) for these choices.

**2.** For other people, declare sets \(F\) and \(S\) that keep them sorted by the first (second) parameter. These sets will be used to make greedy steps further.

**3.** We take the best \(b\) people, replacing previous choices with more optimal ones if needed. Take the object \(A\) with the largest artistique skill. And we have two ways further

- (Greedy) \(\Delta_g\) = the change of answer if we take \(A\) (with the maximal \(y\)) and do not change the previous element of the answer.
- (Replacing) \(\Delta_r\), = the change of answer if we take the maximal \(x\) from the other people' and replace the worst (in terms of penalty) choice in (*).

**4.** Depending on which choice ("greedy" or "replacing) is better we change our sets.

### Online Judges

1. [Коробки (Boxes)](https://www.eolymp.com/en/problems/4701) (problem from Example 1, only Russian statement available)
2. [Dino and fetters](https://www.eolymp.com/en/problems/9640)
3. [Shoemaker Problem](https://www.eolymp.com/en/problems/1591)
4. [Snow White and n gnomes](https://www.eolymp.com/en/problems/2219)
5. [Приключение (Adventure)](https://www.eolymp.com/en/problems/4699) (only Russian statement available) 
6. [Inverse Pairs of Binary Strings](https://codeforces.com/gym/104397/problem/A)
