---
layout: post
title: Sequences of Random Variables
image: /img/hello_world.jpeg
categories:
  - Probability & Statistics
tag: [asymptotic theory, statistics]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
Let $$\Omega$$ be the sample space, {$$X_n$$} the sequence of random variables, {$$x_n$$} the sequence of real numbers, which is a realization of the random variable $$X_n$$ for all n.

## Independent Sequences
A sequence of random variables {$$X_n$$} is mutually independent / jointly independent if and only if:
<p style="text-align: center;">
$$P(\cap_{n=i}^k \{X_i \in A_i\})= \prod_{n=i}^k P(\{X_i \in A_i\})$$
</p>
where $$A_i$$ is a partition on $$\Omega$$.

## IID Sequences
{$$X_n$$} is an IID sequence if and only if it is an **independent sequence** and any two elements of the sequence have the same CDF $$F(x)$$:
\\[\forall x \in \mathbb{R}, \forall i,j \in \mathbb{N}, F_i(x) = F_j(x)\\]

## Stationary Sequences
Let´s split {$$X_n$$} into two groups of sucessive terms, which are $$k$$ positions apart from each other, and denote the joint CDF:
\\[F_{n+1,...,n+q}(x_1,...,x_q)\\]
\\[F_{n+k+1,...,n+k+q}(x_1,...,x_q)\\]
{$$X_n$$} is **strictly stationary** if and only if:
\\[F_{n+1,...,n+q}(x_1,...,x_q)=[F_{n+k+1,...,n+k+q}(x_1,...,x_q)\\]
 $$\forall n,k,q \in \mathbb{N}, \forall (x_n) \in \mathbb{R}^q$$. \\
{$$X_n$$} is **weakly stationary** if and only if:
\\[\exists \mu \in \mathbb{R}: E[X_n] = \mu, \forall n > 0\\]
\\[\forall j \geq 0, \exists \gamma_j \in \mathbb{R}: COV[X_n, X_{n-j}]=\gamma_j, \forall n > j\\]
Therefore, the latter definition shows that only the first two moments are 'stable'.

## Mixing Sequences
Let´s split {$$X_n$$} into two groups of sucessive terms, which are $$k$$ positions apart from each other. The sequence is mixing if the two groups are approximately independent from each other assuming they are far apart. More formally, a sequence is mixing if and only if
\\[\lim \limits_{k \rightarrow \infty}E[f(X_{n+1},...,X_{n+q})g(X_{n+k+1},...,X_{n+k+q})]=E[f(X_{n+1},...,X_{n+q})]E[g(X_{n+k+1},...,X_{n+k+q})]\\]
for any functions $$f, g: \mathbb{R}^q \rightarrow \mathbb{R}$$ and any $$n$$ and $$q$$.\\
Hence, the two random vectors become more and more independent by increasing $$k$$. They can start out as being dependend, though.

## Ergodic Sequences
Let´s define $$\mathbb{R}^{\mathbb{N}}$$ as the set of all possible sequences of real numbers and the subsequence $$\{x_n\}_{n>1} = \{x_2,x_3,...\}$$. Then $$A\subseteq \mathbb{R}^{\mathbb{N}}$$ is shift invariant if and only if:
<p style="text-align: center;">
$$\{x_n\} \in A \implies \{x_n\}_{n>1} \in A$$
</p>
Further, a sequence of random variables $$\{X_n\}$$ is an ergodic sequence if and only if:
<p style="text-align: center;">
$$P(\{X_n\} \in A) = 0$$ or $$P(\{X_n\} \in A)=1$$
</p>
whenever $$A$$ is a shift invariant set.

## Final Note
* $$IID \implies \text{Strict Staionarity} \implies \text{Weak Stationarity (if exists)}$$
* $$IID \implies \text{Mixing}$$
