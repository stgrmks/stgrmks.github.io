---
layout: post
title: Generalized Linear Models
image: /img/hello_world.jpeg
categories:
  - Statistics
tag: [Linear Regression, OLS]
---
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## Introduction
In linear regression we estimate the following relationship:
<p style="text-align: center;">
$$\mu = X'\beta$$
</p>
where $$E[Y] = \mu$$. The GLM framework generalizes this concept to estimate the following relationship,
<p style="text-align: center;">
$$\eta =  g(\mu) = X'\beta$$
</p>
where $$\eta$$ transforms the mean!\\
The general framework can be defined as follows:
<p style="text-align: center;">
$$\eta_i = g(\mu_i) = x'_i\beta$$
$$E[y_i] = \mu_i = f(\theta)$$
</p>
The former equation is known as the link function and relates the linear regression to the mean. The latter equation emphasizes the dependency of the mean on the model parameters. This will hold if any distribution of the exponential family is used. Hence, the GLM framework assumes a distribution from the exponential family. The resulting model is defined by:
<p style="text-align: center;">
$$Y_i = g^{-1}(\mu_i) + \epsilon_i$$
</p>
where $$\epsilon_i$$ is iid and follows some distribution from the exponential family.

## Canonical Form
Any distribution from the exponential family can be factorized into the canonical form:
<p style="text-align: center;">
$$f(y_i;\theta_i) = exp\{ a(y_i)\underbrace{b(\theta_i)}_{\text{natural parameter}} + c(\theta_i) +d(y_i) \}$$
</p>

## Examples
Both examples do not need to link the mean to the distribution parameter explicitely. This is not always the case! In some cases, the link function depends on the natural parameter and must be adjusted to properly link the quantity we are interest in to the distribution parameters. In other cases, the link function is custom.

### Poisson Regression
<p style="text-align: center;">
$$f(y_i;\lambda_i) = \frac{\lambda_i^{y_i}e^{-\lambda_i}}{y_i!} = exp\{\underbrace{y_i ln(\lambda_i)}_{a(y_i)b(\theta_i)} - \lambda_i - ln(y_i!)\}$$
$$E[y_i] = \mu_i = \lambda_i$$
</p>
Hence, the mean is transformed and linked to the regression as follows:
<p style="text-align: center;">
$$g(\mu_i)=ln(\mu_i)=x'_i\beta$$
</p>
If the mean equals the parameter, the natural parameter from the canonical form can be used as a link function between the transformed mean and the (linear) regression. Now, using the maximum likelihood principle to derive a first order condition, which must be optimized on way or another.
<p style="text-align: center;">
$$l_i(\beta;y_i) = exp\{ y_i x'_i\beta -e^{x'_i\beta} -ln(y_i!) \})$$
$$L(\beta;Y) = ln(\prod_i l_i(\beta;y_i)) = \sum_i y_i x'_i\beta -e^{x'_i\beta} -ln(y_i!)$$
</p>
where the first equation is the likelihood function over a single obversation and the latter one is the complete log-likelihood function. Now, we can compute the first derivative:
<p style="text-align: center;">
$$\frac{d}{d\beta}L(\beta;Y) = \sum_i y'_i x_i -x_i e^{x'_i\beta} \overset{!}{=}0$$
</p>
The above expression is not solveable analytically. Hence, some optimization algorithm must be applied.

### Logistic Regression
<p style="text-align: center;">
$$f(y_i;\pi_i) = \pi_i^{y_i}(1-\pi_i)^{1-y_i} = exp\{y_i ln(\pi_i) + (1-y_i)ln(1-\pi_i)\} = exp\{\underbrace{y_i ln(\frac{\pi_i}{1-\pi_i})}_{a(y_i)b(\theta_i)} + ln(1-\pi_i)\}$$
$$E[y_i] = \mu_i = \pi_i $$
</p>
Hence, the mean is transformed and linked to the regression as follows:
<p style="text-align: center;">
$$g(\mu_i)=ln\big(\frac{\mu_i}{1-\mu_i}\big)=x'_i\beta$$
</p>
This link function models log-odds or logits. Now, the maximum likelihood estimation is analog to the previous case and the first order condition turns out to be:
<p style="text-align: center;">
$$\frac{d}{d\beta}L(\beta;Y) = \sum_i y'_i x_i - \sum_i x_i \frac{e^{x'_i\beta}}{1+e^{x'_i\beta}} \overset{!}{=}0$$
</p>
Again, not solveable analytically.

## General Maximum Likelihood Estimation
This section assumes knowledge of properties of distributions belonging to the exponential family.
<p style="text-align: center;">
$$ln(l_i(\theta_i; y_i)) = y_i b(\theta_i) + c(\theta_i) + d(y_i)$$
</p>
where $$a(y_i) = y_i$$ is assumed for simplicity. Furthermore,
<p style="text-align: center;">
$$E[y_i] = \mu_i = -\frac{c'(\theta_i)}{b'(\theta_i)}$$
$$Var(y_i) = \frac{b''(\theta_i)c'(\theta_i-c''(\theta_i)b'(\theta_i))}{[b'(\theta_i)]^3}$$
$$\eta_i = g(\mu_i)=x'_i \beta$$
$$\mu_i = g^{-1}(\eta_i)$$
</p>
The full log-likelihood based on a distribution from the exponential family can be defined as:
<p style="text-align: center;">
$$L(\theta;Y) = ln(\prod_i l_i(\theta_i; y_i)) = \sum_i y_i b(\theta_i) + c(\theta_i) + d(y_i)$$
</p>
Now, we derive the first order condition for a single parameter for simplicity:
<p style="text-align: center;">
$$\frac{\partial (L)}{\partial \beta_j} = \sum_i \frac{\partial (l_i)}{\partial \theta_i} \frac{\partial \theta_i}{\partial \mu_i} \frac{\partial \mu_i}{\partial \beta_j}$$
</p>
Breaking the computation into smaller parts as follows:
<p style="text-align: center;">
$$\frac{\partial (L)}{\partial \theta_i} = y_i b'(\theta_i) + c'(\theta_i) = y_i b'(\theta_i) - \mu_i b'(\theta_i) = b'(\theta_i)(y_i - \mu_i)$$
$$\frac{\partial \theta_i}{\partial \mu_i} = \frac{1}{\frac{\partial \mu_i}{\partial \theta_i}} = - \frac{c''(\theta_i)b'(\theta_i)+b''(theta_i)c'(\theta_i)}{[b'(theta_i)]^2} = b'(\theta_i)Var[y_i]$$
$$\frac{\partial \mu_i}{\partial \beta_j} = \frac{\partial \mu_i}{\partial \eta_i} \frac{\partial \eta_i}{\partial \beta_j} = \frac{\partial \mu_i}{\partial \eta_i}x_{ij}$$
</p>
Putting everything together:
<p style="text-align: center;">
$$\frac{\partial (L)}{\partial \beta_j} = \sum_i \frac{b'(\theta_i)(y_i - \mu_i)}{b'(\theta_i)Var[y_i]} \frac{\partial \mu_i}{\partial \eta_i} x_{ij} = \sum_i \frac{(y_i - \mu_i)}{Var[y_i]} \frac{\partial \mu_i}{\partial \eta_i} x_{ij} \overset{!}{=}0$$
</p>

## TODOS
Derive variance :)
