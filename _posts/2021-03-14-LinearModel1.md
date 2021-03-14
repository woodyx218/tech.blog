---
layout: post
title: Linear Models - OLS Optimization and Statistics
watch: true
excerpt: Introduction to OLS, its optimization issues and statistics, which motivated my researches.
image:
    path: images/linear1.png
    width: 70%
tags: statistics optimization linear_model high_dimension
---


## Introduction to OLS
Linear models is one of the most fundamental models in machine learning. Even though they have been studied for decades, there still exist surprising facts awaiting discovery. And I am sure in this post, you will find something you didn't know before.

Consider a linear regression **model**

$$y=X\beta+\epsilon$$

Here $y\in\mathbb{R}^n$ is the response or the label, $X\in\mathbb{R}^{n\times p}$ is the data matrix or measurement, $\beta\in\mathbb{R}^p$ is the unknown parameter we are interested in and $\epsilon$ is some random noise.

How do we learn the parameters $\beta$? We need to formulate **problems**.

Some problems include the ordinary least squares (OLS), LASSO, Ridge, Elastic Net...

Let's start with the simplest problem: OLS

$$\min_{b} \frac{1}{2}\|y-Xb\|^2$$

### Optimization
There are two **approaches** to learn the parameters $\beta$ through the OLS optimization problem:

1. closed-form solution $\hat\beta=(X^\top X)^{-1}X^\top y$
2. iterative solution, e.g. through gradient descent $\hat\beta_{t+1}=\hat\beta_t-\eta X^\top(X\hat\beta_t-y)$

Furthermore, each approach can have several **methods** to carry out. For example, gradient descent, stochastic gradient descent, Adam, Heavy Ball are all different methods (a.k.a. optimizers) for the second approach.

Usually, we have $\hat\beta_t\to\hat\beta$. *But this does not make these two approaches equivalent!*

The first approach can be problematic if

(1) $X$ contains multi-collinearity, hence $(X^\top X)^{-1}$ is not well-defined;

(2) Inverse of $X^\top X$ can be difficult to compute due to complexity issues (memory, speed...)

The second approach is widely used in many programming libraries but still have some issues. For one thing, $\hat\beta_t$ may not converge if the step size, or the learning rate $\eta$ is not properly chosen. Also, since gradient descent iteratively approximates the true minimizer, it induces some error along the way.

In more advanced topics, such as the differential privacy field, these two approaches has dramatically different privacy guarantee when learning the OLS. The interested readers can check [this paper](https://arxiv.org/abs/1803.02596) for details. The difference is highly non-trivial.

There is a case that both approaches fail, which renders OLS itself not a good problem --- the high dimension $(p>n)$.

### OLS in high dimension
In statistical machine learning, high dimensional data means $(p>n)$ instead of $p$ being large. I.e. $X\in\mathbb{R}^{3\times 4}$ is a high-dimensional data but $X\in\mathbb{R}^{10000\times 9999}$ is low-dimensional.

In low dimension, OLS minimizer is unique and enjoys many good statistical properties, which I will shortly describe. Especially, this unique OLS $\hat\beta$ converges to the truth $\beta$. 

In high dimension, there are infinitely many OLS minimizers, all achieving zero MSE loss and can be far away from the truth $\beta$. In other words, even if you have a large number of samples, the OLS minimizer may not be close to the truth. Intuitively, if you have $X\in\mathbb{R}^{9999\times 10000}$, then you have 9999 linear equations with 10000 unknown variables $\hat\beta_j$, leaving you 1 degree of freedom and thus infinitely many solutions.

This is part of the reason that we need regularization and problems such as LASSO. I will talk about these problems in a separate post. (link to be added??)

### Statistics
Fortunately, OLS has been studied extensively and, due to its closed form, we can characterize many of its statistical behaviors. These include:

1. statistical consistency (in fact $\hat\beta\to\beta$ as $n\to\infty$, at rate $1/\sqrt{n}$)
2. bias and standard deviation (and confidence interval of $\hat\beta$)
3. asymptotic normality
4. prediction interval

See [Wiki: Proofs of OLS](https://en.wikipedia.org/wiki/Proofs_involving_ordinary_least_squares) for some details.

However, we remark that OLS is a very special problem of linear regression, in the sense that most other problems (e.g. LASSO, Group LASSO, SLOPE) do not have closed-form solutions. This situation makes the analysis of LASSO difficult. Even though LASSO was proposed in 1996, I still publish at [NeurIPS spotlight 2020](https://papers.nips.cc/paper/2020/hash/e7db14e12fb49c1d78a573e6e5f542c2-Abstract.html) on its statistical analysis in high dimension.

## Tips for Research
It is important to clearly understand the components in research: 

$$model\to problem\to approach\to methods\to theory$$

A brilliant work can focus on any of these components and usually is a blend of two to three components. For example, generative adversarial network (GAN) promotes a new model and a new optimization problem to learn it; Heavy Ball is a significant work on the methods; NTK provides a convergence theory for existing optimizers on existing optimization problems of existing neural networks.
