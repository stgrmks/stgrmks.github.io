---
layout: post
title: Stochastic Convergence
image: /img/hello_world.jpeg
categories:
  - Probability & Statistics
tag: [asymptotic theory, statistics]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
## Pointwise / Sure Convergence
Let´s $$\{X_n\}$$ a sequence of random variables defined on a sample space $$\Omega$$, where a single sample point is denoted as $$\omega \in \Omega$$. Further note, that a single RV is a function $$X_n: \Omega \rightarrow \mathbb{R}$$.\\
$$\{X_n\}$$ is pointwise convergent to some RV $$X$$ defined on $$\Omega$$ if and only if:
<p style="text-align: center;">
$$\{X_n(\omega)\} \rightarrow X(\omega)$$
</p>
$$\forall \omega \in \Omega$$.
Please note that using pointwise convergence circumvents the problem of defining distances between RV. We simply check for convergence of sequences of real numbers, since $$\omega$$ is fixed.\\
**Example**: The sample space is defined as $$\Omega = \{\omega_1,\omega_2\}$$. $$\{X_n\}$$ is a sequence of RV and
<p style="text-align: center;">
$$X_n(\omega) = \left\{
        \begin{array}{ll}
            \frac{1}{n} & if \omega = \omega1 \\
            1+\frac{2}{n} & if \omega = \omega2
        \end{array}
    \right
    .$$
</p>
It is trivial to find the limits; at least if there are just two sample points:
<p style="text-align: center;">
$$X(\omega) = \left\{
        \begin{array}{ll}
            0 & if \omega = \omega1 \\
            1 & if \omega = \omega2
        \end{array}
    \right
    .$$
</p>
## Almost Sure Convergence
A sequence $$\{X_n\}$$ converges almost surely to some random variable $$X$$ if and only if:
<p style="text-align: center;">
$$P(\omega \in \Omega: \lim \limits_{n \rightarrow \infty} |X_n(\omega)-X(\omega))=1$$
$$X_n(\omega) \overset{a.s.}{\rightarrow} X(\omega)$$

</p>
A.s. convergence requires the sequence to converge for all sample points $$\omega \in \Omega$$ except for some set $$F^c$$ of sample points. Note, $$F^c$$ must belong to a zero-probability event! See post about probability fundamentals for more details.
## Mean-Square Convergence
$$\{X_n\}$$ is a sequence of **square integrable** RV defined on the sample space $$\Omega$$. The sequence is mean-square convergent if and only if the **moment $$E[(X_n-X)^2]$$ exists** and fulfills:
<p style="text-align: center;">
$$\lim \limits_{n \rightarrow \infty}E[(X_n-X)^2]=0$$
$$X_n(\omega) \overset{m.s.}{\rightarrow} X(\omega)$$
</p>
This means basically a convergence in the first and second moments. Thus, $$COV[X_n,X]=1$$.
## Convergence in Probability
Let´s call $$\{X_n\}$$ to be convergent in probability to some random variable $$X$$; both defined on a sample space $$\Omega$$ if and only if:
<p style="text-align: center;">
$$P(|X_n - X|>\epsilon)=0$$
</p>
$$\forall \epsilon > 0$$. Further note that $$X$$ is the probability limit of the sequence and is denoted as:
<p style="text-align: center;">
$$X_n \overset{P}{\rightarrow}X$$
</p>
or
<p style="text-align: center;">
$$\underset{n \rightarrow \infty}{\text{plim}}(X_n) =X$$
</p>
Hence, the realizations of $$X_n$$ get closer to the realizations of $$X$$ as $$n \rightarrow \infty$$. Usually **WLLn** or **Chebyshev´s Inequality** is applied.

## Convergence in distribution
A sequence of RV $$\{X_n\}$$ is said to be convergent in distribution to $$X$$ if and only if there exists a CDF $$F_{X}(x)$$ such that the sequence $$\{F_{X_n}(x)\}$$ converges to $$F_{X}(x)$$:
<p style="text-align: center;">
$$\lim \limits_{n \rightarrow \infty} F_{X_n}(x) = F(x)$$
$$X_n \overset{d}{\rightarrow}X$$
</p>
$$\forall x \in \mathbb{R}$$ at which F is continuous.\\
Thus, the realizations of $$X_n$$ and $$X$$ may differ, but the distributions are similar. Best example is CLT. Further note, that the RV do **not** need to be **defined** on the same sample space $$\Omega$$, unlike all previously introduced convergence modes.

## References
-
