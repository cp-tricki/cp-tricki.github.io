---
title: Translate DP to the matrix form
---

### Short description

Sometimes, we can rewrite our dynamic programming transition formulae using matrices and operations between them (most remarkably multiplication). Then, we can exploit this form in some way.

### Prerequisites 

Basic familiarity with dynamic programming and matrices (linear algebra in general does not required).

### General description 

We shall not follow the most general setting here, instead focusing on the following DP (linear rerecurrenceelation):

\[
	dp_n = a_1 dp_{n-1} + a_2 dp_{n-2} + \dots + a_k dp_{n-k}.
\]

Then, one can notice that the right hand side can be expressed as dot prothe duct

\[
	a_1 dp_{n-1} + \dots + a_k dp_{n-k} = 
	\begin{pmatrix}
		a_1 & a_2 & \dots & a_k
	\end{pmatrix}
	\begin{pmatrix}
		dp_{n-1} & dp_{n-2} & \dots & dp_{n-k}
	\end{pmatrix}^T.
\]

These vectors on their own are very natural: the first one is our coefficients and the second one keeps our recent values of DP. 
The key idea now is to obtain the next vector of recent values, namely \( \begin{pmatrix} dp_n & dp_{n-1} & \dots & dp_{n-k+1} \end{pmatrix}^T \). 
To do so, we need to apply our previous relation, and then shift all the other values (as well as eliminate \(dp_{n-k}\) because we will not need it further).
Is it actually easy to shift, so we have the following identity 

\[
	\begin{pmatrix}
		dp_{n}\\
		dp_{n-1}\\
		\vdots\\
		dp_{n-k+2}\\
		dp_{n-k+1}
	\end{pmatrix} =
	\begin{pmatrix}
		a_1    & a_2    & \dots  & a_{k-1} & a_k\\
		1      & 0      & \dots  & 0       & 0\\
		0      & 1      & \dots  & 0       & 0\\
		\vdots & \vdots & \ddots & \vdots  & \vdots\\
		0      & 0      & \dots  & 1       & 0
	\end{pmatrix}
	\begin{pmatrix}
		dp_{n-1} \\
		dp_{n-2} \\
		\vdots\\
		dp_{n-k+1}\\
		dp_{n-k}
	\end{pmatrix}
\]

Or, in a more compact form (\(A\) is the large matrix on the left hand side)

\[
	recent_n = A~recent_{n-1},
\]

where \(recent_n\) is the vector \((dp_n, dp_{n-1}, \dots, dp_{n-k+1}\) which contains the last \(k\) dp values. 
We can inductively deduce

\[
	recent_n = A recent_{n-1} = A^2 recent_{n-2} = \dots = A^{n-k+1} recent_{k-1}.
\]

Matrix multiplication can be done in \(O(k^3)\), and using binary exponentiation we obtain \(O(k^3 \log n)\) algorithm.

### Example 1 (+constant)

Given \(dp_n = A dp_{n-1} + B dp_{n-2} + C\), find \(dp_N\) in \(O(\log N)\) time. 

We can use the same idea here,

\[
	\begin{pmatrix}dp_n dp_{n-1} C\end{pmatrix} = \begin{pmatrix}A & B & 1\end{pmatrix} \begin{pmatrix} dp_{n-1} & dp_{n-2} & C \end{pmatrix}
\]

only adding a column to our transition matrix and the constant to our \(recent_n\) vector.

### Example 2 (twisted DPs)

Sometimes one needs to evaluate several twisted but simple DPs, something like (some random relations just for the sake of illustration):

\[
	dp^1_i = f(dp^1_{i-1}, dp^1_{i-2}, dp^2_{i-1}, dp^3_{i-2}),
\]

\[
	dp^2_i = g(dp^1_{i-1}, dp^2_{i}, dp^2_{i-1}, dp^2_{i-2}),
\]

\[
	dp^3_i = h(dp^2_{i-2}, dp^3_{i-1}).
\]

Then one can also use some kind of matrix transformation but with more convoluted \(recent\) vectors.
