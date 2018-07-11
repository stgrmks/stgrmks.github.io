---
layout: post
title: Exponential Family
image: /img/hello_world.jpeg
categories:
  - Statistics
tag: [Fundamentals]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## Introduction
Let´s define $$y$$ as a RV, which depends on parameter $$\theta$$. The distribution of $$y$$ belongs to the exponential family iff it can be rewritten in the canonical form as follows:
<p style="text-align: center;">
$$f(y;\theta)=s(y)t(\theta)e^{a(y)b(\theta)} = exp\{a(y)b(\theta)+\underbrace{ln(t(\theta))}_{c(\theta)} + \underbrace{ln(s(y))}_{d(y)}\}$$
</p>
Please note that $$b(\theta)$$ is the so called natural parameter and $$a(y)$$ is usually $$a(y)=y$$.

## Examples

### Poisson distribution
<p style="text-align: center;">
$$f(y;\theta)=\frac{\theta^y e^{-\theta}}{y!}=exp\{\underbrace{yln(\theta)}_{a(y)b(\theta)}-\underbrace{\theta}_{c(\theta)} - \underbrace{ln(y!)}_{d(y)}\}$$
</p>

### Normal Distribution
Note that $$\sigma$$ is fixed in this example.
<p style="text-align: center;">
$$f(y;\mu)=\frac{1}{\sqrt{2\pi \sigma^2}}e^{-\frac{1}{2\sigma^2}(y-\mu)^2} = exp\{ \underbrace{-ln(\sqrt{2\pi \sigma^2}}_{\text{nuisance term}} \underbrace{-\frac{y^2}{2\sigma^2}}_{d(y)} \underbrace{-\frac{\mu^2}{2\sigma^2}}_{b(\theta)} \underbrace{-\frac{2y\mu}{2\sigma^2}}_{a(y)b(\theta)} \}$$
</p>

## Properties
Let´s start with the following basic property:
<p style="text-align: center;">
$$\int_y f(y;\theta)dy=1 $$
$$\frac{d}{d\theta}\int_y f(y;\theta)dy=0$$
</p>
Now, assuming we can interchange the integral with the derivative, we get the following properties:
<p style="text-align: center;">
$$\int_y \frac{d}{d\theta} f(y;\theta)dy=0 $$
$$\int_y \frac{d^2}{d\theta^2} f(y;\theta)dy=0 $$
</p>
Applying these properties on the exponential family reveals some interesting relationships:
<p style="text-align: center;">
$$\frac{d}{d\theta}f(y;\theta)=[a(y)b'(\theta)+c'(\theta)]f(y;\theta)$$
</p>
Note that $$b'(\theta)=\frac{d}{d\theta}b(\theta)$$. Now, evaluating the general properties yields:
<p style="text-align: center;">
$$\int_y \frac{d}{d\theta} f(y;\theta)dy=\int_y [a(y)b'(\theta)+c'(\theta)]f(y;\theta) dy = 0 $$
</p>
Some rearranging:
<p style="text-align: center;">
$$b'(\theta)E[a(y)]+c'(\theta) = 0 $$
$$E[a(y)] = -\frac{c'(\theta)}{b'(\theta)}$$
</p>
It is probably not a surprise that the (possible transformed) mean is a function of the parameter! More specifically, a function of the first derivative of the natural parameter. A similar relationship can be uncovered if the second derivative is evaluated. We essentially end up with the variance:
<p style="text-align: center;">
$$Var[a(y)] = \frac{b''(\theta)c'(\theta)-c''(\theta)b'(\theta)}{[b'(\theta)]^3}$$
</p>

## Maximum Likelihood Estimation
Equipped with the previous properties, we can dig into the properties of the log-likelihood, which is the basis for MLE. In order to simplify the notation we evaluate the properties only for a single obversation. Normally, the likelihood would be computed for all observations. Let´s start with the log-likelihood for a distribution that belongs to the exponential family:
<p style="text-align: center;">
$$l(\theta;y)=a(y)b(\theta)+c(\theta)+d(y)$$
</p>
We maximize w.r.t. the parameter to identify the data generating process (most likely data generating process); we compute the score:
<p style="text-align: center;">
$$S = \frac{d}{d\theta}l(\theta;y) = a(y)b'(\theta)+c'(\theta) \overset{!}{=} 0 $$
</p>
Taking expections w.r.t. to the RV:
<p style="text-align: center;">
$$E[S] = \int_y [a(y)b'(\theta)+c'(\theta)]f(y;\theta)dy = b'(\theta)E[a(y)] + c'(\theta) = b'(\theta)\big(-\frac{c'(\theta)}{b'(\theta)}\big) + c'(\theta) = 0$$
</p>
and computing the variance in case we want to derive the asymptotic distribution later:
<p style="text-align: center;">
$$Var[S] = b''(\theta)Var[a(y)] = \frac{b''(\theta)c'(\theta) - c''(\theta)}{b'(\theta)}$$
</p>
Interestingly, we sometimes can have an easier computation by using the first derivative of the score:
<p style="text-align: center;">
$$\int_y \frac{d\big(S\big)}{d\theta} f(y;\theta) dy = \int_y \frac{d^2\big(l(\theta;y)\big)}{d\theta^2} f(y;\theta)dy = -b''(\theta)\frac{c'(\theta)}{b'(\theta)} + c''(\theta) = - Var[S]$$
</p>

## Asymptotic Normality
As derived in the MLE post, the asymptotic distribution can be defined as follows:
<p style="text-align: center;">
$$\sqrt{N}(\hat\theta - \theta) \overset{d}{\rightarrow} \mathcal{N}(0, Var[S]^{-1})$$
</p>
where $$\hat\theta = argmax_{\theta \in \Theta} L(\theta;y)$$. Note that $$L(\theta;y)$$ is the proper likelihood function over all observations!
