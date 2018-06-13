---
layout: post
title: Primer on Probability
image: /img/hello_world.jpeg
categories:
  - Probability Theory
tag: [Fundamentals]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## The Environment
* Probability always refers to some event in the sample space $$E \subseteq \Omega$$.
* Probability is a real number.

### Sample space
Contains all possible outcomes $$\omega \in \Omega$$, where $$\omega$$ is a single possible outcome and $$\bar\omega \in \Omega$$ is a realized outcome.

### Space of Events
Contains all events and is usually denoted as:
<p style="text-align: center;">
$$\mathcal{F}=\{E, F, \Omega, \emptyset\}$$
</p>
where $$E$$, $$F$$ and $$\Omega$$ could be defined as follows:
<p style="text-align: center;">
$$\Omega=\{1,2,3,4,5,6\}$$
$$E=\{1,3,5\}$$
$$F=\{2,4,6\}$$
</p>
which essentially defines a few events on a dice.

## Properties
1. Range: $$0\leq P(E) \leq 1$$
2. Sure Outcome: $$P(\Omega)=1$$
3. Sigma-Additivity: $$P(\bigcup\limits_{n=1}^{\infty}E_n)=\sum^{\infty}_{n=1}P(E_n)$$\\
for any mutually exclusive events, such that $$E_i \cap E_j = \emptyset$$ if $$i \neq j$$.

## Zero-Probability events
The easiest way to introduce this concept is by an example:\\
Let´s define the space of events $$\Omega=[0,1]$$ on the unit interval. Further, let´s create a subinterval $$[a,b] \subseteq \Omega$$ and define a probability function $$P([a,b])=b-a$$ that defines the probability as the interval length.\\
Now, we define some event:
<p style="text-align: center;">
$$E=\{\omega \in \Omega: \omega \text{ is a rational number}\}$$
</p>
It is important to note that $$E$$ is countable! Thus, $$P(\omega)=0$$!
<p style="text-align: center;">
$$P(E)=P(\bigcup^{\infty}_{n=1}\omega_n)=\sum^{\infty}_{n=1}\omega_n=0$$
</p>
Therefore, $$E$$ is a zero-probability event! Further defining another events,
<p style="text-align: center;">
$$F=\{\omega \in \Omega: \omega \text{ is an irrational number}\}$$
</p>
and now computing,
<p style="text-align: center;">
$$P(F)=P(E^c)=1-P(E)=1$$
</p>
where $$E^c$$ is the complementary event of $$E$$.

## Independence
If two events $$E$$ and $$F$$ are independent then information about the conditioned variable does not change the probability of the event:
<p style="text-align: center;">
$$P(E \cap F)=P(E)P(F)$$
$$P(E|F)=\frac{P(E \cap F)}{P(F)}=\frac{P(E)P(F)}{P(F)}=P(E)$$
$$P(F|E)=P(F)$$
</p>
A more generalized for can be stated as follows: Let $$E_1,...,E_n$$ are jointly/mutually independent if and only if for **any sub-collection of k events** ($$k \leq n$$) $$E_{i1},...,E_{ik}$$:
<p style="text-align: center;">
$$P(\cap_j E_{ij})=\prod_j P(E_{ij})$$
</p>
Thus, simply checking if this equation holds is enough to determine independence. However, it is important to note that only checking couples is not sufficient:
<p style="text-align: center;">
$$P(E_1 \cap E_2)=P(E_1)P(E_2) \wedge P(E_1 \cap E_3)=P(E_1)P(E_3) \wedge P(E_2 \cap E_3)=P(E_2)P(E_3)$$
$$\text{does not imply}$$
$$P(E_1 \cap E_2 \cap E_3)=P(E_1)P(E_2)P(E_3)$$
</p>
## Bayes Rule
<p style="text-align: center;">
$$P(A|B)=\frac{P(B|A)P(B)}{P(B)}=\frac{P(B|A)P(B)}{\sum_A P(B|A)P(A)}$$
</p>
where $$P(A|B)$$ is the **posterior probability**, $$P(B|A)$$ is the **likelihood**, $$P(A)$$ is the **prior probability** and $$P(B)$$ is the **marginal probability**.
## References
-
