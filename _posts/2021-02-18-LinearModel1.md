---
layout: post
title: Linear Models - OLS Optimization and Statistics
watch: true
excerpt: Introduction to linear models, their optimization and statistical analysis, which motivates my researches.
image:
    path: images/amp1.png
    width: 70%
categories: statistics optimization linear_model high_dimension
---
<script type="text/x-mathjax-config"> MathJax.Hub.Config({ TeX: { equationNumbers: { autoNumber: "all" }, extensions:["color.js"] } }); </script>
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            processEscapes: true
        }
    });
</script>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>


# Background
Linear models is one of the most fundamental models in machine learning. Even though they have been studied for decades, there still exist surprising facts awaiting discovery. And I am sure in this post, you will find something you didn't know before.

Consider a linear regression **model**
$$y=X\beta+\epsilon$$
Here $y\in\mathbb{R}^n$ is the response or the label, $X\in\mathbb{R}^{n\times p}$ is the data matrix or measurement, $\beta\in\mathbb{R}^p$ is the unknown parameter we are interested in and $\epsilon$ is some random noise.

How do we learn the parameters $\beta$? We need to formulate **problems**.

Some problems include the ordinary least squares (OLS), LASSO, Ridge, Elastic Net...

Let's start with the simplest problem: OLS
$$\min{b}\frac{1}{2}\|y-Xb\|^2$$

We will talk about other problems in a separate post. (link to be added)

There are two approaches to learn the parameters $\beta$

Take the simplest OLS as an example, traditional statistics theory allows us to learn $\beta$ (either through the closed-form $(X^\top X)^{-1}$ or through iterative algorithms such as gradient descent) as well as to characterize its statistical behaviors. These include the statistical consistency and asymptotic normality. See [Wiki: Proofs of OLS](https://en.wikipedia.org/wiki/Proofs_involving_ordinary_least_squares) for details.

Naturally, we want 

