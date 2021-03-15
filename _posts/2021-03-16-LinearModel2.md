---
layout: post
title: Linear Models - LASSO Optimization and Statistics
watch: true
excerpt: Introduction to the sparse solution LASSO and L1 regularization, from optimization and statistical analysis points of view.
image:
    path: ../images/linear_equation.png
    width: 70%
tags: statistics optimization linear_model high_dimension regularization
---


# Introduction to LASSO
LASSO is the combination of L1 regularization and linear regression ($y=X\beta+\epsilon$). If we change L1 regularization to others, then we get a different problem (e.g. sorted L1 norm regularization is the SLOPE problem; L2 norm regularization is Ridge). Similarly, if we change linear regression to a neural network, then we end up with a sparse network.

We first introduce the L1 regularization (or the L1 penalty), starting from the L1 norm.

# What is L1 regularization?
Given a verctor $x$, one can compute the $L_p$ norm

$$\left\|x\right\|_{p}=\left(|x_{1}|^{p}+|x_{2}|^{p}+\cdots +|x_{n}|^{p}\right)^{1/p}.$$

Then L1 norm is simply the sum of absolute values of entries in $x$.

Now we return to the OLS problem, which is an unconstrained optimization problem:

$$\min_b \frac{1}{2}\|y-Xb\|^2$$

We can set the L1 constraint on the problem to get the *Lasso problem (constraint definition)*:

$$\begin{align}
\min_b &\frac{1}{2}\|y-Xb\|^2
\\
\text{s.t.} &\|b\|_{1} \leq t
\end{align}
$$
Or equivalently the *Lasso problem (penalty definition)*,
$$
\begin{align}
\min_b &\frac{1}{2}\|y-Xb\|^2+\lambda\cdot\|b\|_1
\end{align}
$$

This equivalence between constraint and penalty definitions also generally holds for other norm regularization. E.g.
$$
\begin{align}
\begin{cases}
\min_b &\frac{1}{2}\|y-Xb\|^2
\\
\text{s.t.} &\text{norm}(b) \leq t
\end{cases}
\Longleftrightarrow
\min_b &\frac{1}{2}\|y-Xb\|^2+\lambda\text{norm}(b)
\end{align}
$$

# Why do we apply L1 regularization?
why use any regularization?

# When can we apply L1 regularization?

# Can we conduct statistical inference on Lasso?

# Tips for Research
