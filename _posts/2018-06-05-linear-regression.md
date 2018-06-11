---
layout: post
title: Linear Regression
image: /img/hello_world.jpeg
categories:
  - Econometrics
tag: [ols, linear_regression]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
## Introduction
-
## Model
<!-- \\(\vec Y = \vec X^T \vec\beta + \vec U\\)  -->
\\(y = x^T \beta + u\\)\\
with:\\
\\(x \in \mathbb{R}^{KxN}\\),\\
\\(\beta \in \mathbb{R}^{Kx1}\\),\\
\\(u, y \in \mathbb{R}^{Nx1}\\)
## Assumptions
1. $$E[xu]=0$$\\
First note that $$E[u|x]=E[u]$$ if and only if $$u \perp x$$:
\\[E[u|x] = \int u \frac{f(u,x)}{f(x)}du = \int u \frac{f(u)f(x)}{f(x)}du = \int u f(u) du = E[u] = 0\\]
Further note that $$E[u|x] = 0 \implies E[xu]=0$$:
\\[COV(u,x)=E[(x-E[x]) (u-E[u])]=E[xu] - E[x]E[u]=E[xu]\\]
Therefore, u has a zero mean and is uncorrelated with any regressors.
2. rk(E[$$x^T x$$])=K \\
Full rank is needed for identification. Ensures that the estimate of $$\beta$$ are unique.
3. Homoskedasticity
Means that all coeffcients follow the same variance in the population.
\\[E[xu(xu)^T] = \sigma^2 E[xx^T] = \sigma^2 A\\]
See asymptotic properties section.

## Parameter Identification
Starting point is the squared error:
\\[u^T u = (y - \hat{y})^T (y - \hat{y}) = (y - x^T \beta)^T (y - x^T \beta)=y^T y - 2y^T x^T \beta + \beta^T xx^T \beta \\]
Taking partial derivative w.r.t. $$\beta$$:
\\[\frac{\partial u^T u}{\partial \beta^T} = --2xy + 2xx^T \beta \overset{!}{=} 0\\]
And solving for $$\beta$$:
\\[\hat{\beta} = (xx^T)^{-1}xy \\]

## Asymptotic Properties
\\[\hat{\beta} = (xx^T)^{-1}xy = (xx^T)^{-1}xx^T \beta + (xx^T)^{-1}xu = \beta + (xx^T)^{-1}xu\\]
Replacing the moments with the corresponding sample averages:
\\[\hat{\beta} = \beta + (N^{-1} \sum_i x_i x_i^T)^{-1}(N^{-1} \sum_i x_i u_i)\\]
Rewritting and normalizing to use CLT:
\\[(\sqrt{N}(\hat{\beta}-\beta) = \sqrt{N}(N^{-1} \sum_i x_i x_i^T)^{-1}(N^{-1} \sum_i x_i u_i)\\]
Splitting the right side and analysing the asymptotic behaviour. The first one:
\\[E[N^{-1} \sum_i x_i x_i^T] \overset{iid}{=} E[x_i x_i^T] \equiv A^{-1} \\]
\\[\lim \limits_{n \rightarrow \infty}  VAR[N^{-1} \sum_i x_i x_i^T] \overset{iid}{=} N^{-1} VAR[x_i x_i^T] = 0\\]
The second one:
\\[E[N^{-1/2} \sum_i x_i u_i] \overset{iid}{=} N^{1/2} E[x_i u_i] = 0 \\]
\\[\lim \limits_{n \rightarrow \infty}  VAR[N^{-1/2} \sum_i x_i u_i] \overset{iid}{=}N^{-1/4}NVAR[x_i u_i] = N^{3/4}E[x_i u_i (x_i u_i)^T] - E[x_i u_i] E[x_i u_i]^T = E[x_i u_i u_i^T x_i^T] \equiv B \\]
Hence:
\\[N^{-1} \sum_i x_i x_i^T  \overset{p}{\to} A^{-1}\\]
\\[N^{-1/2} \sum_i x_i u_i^T  \overset{d}{\to} \mathcal{N}(0,B)\\]
Thus, we can determine the asymptotic distribution as follows:
\\[\sqrt{N} (\hat{\beta}-\beta) \overset{p}{\to} A^{-1}\mathcal{N}(0,B) = \mathcal{N}(0,A^{-1}BA^{-1})\\]
\\[\hat{\beta} \overset{a}{\thicksim} \mathcal{N}(\beta,\frac{A^{-1}BA^{-1}}{N}) \\]
Therefore, the estimator is consistent.
## Code
~~~python
s = "TO BE DONE"
print s
~~~
