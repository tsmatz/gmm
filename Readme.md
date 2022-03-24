# Estimation in Gaussian Mixture Model (GMM)

In this repository, I'll introduce 2 methods for Gaussian Mixture Model (GMM) estimation - **EM algorithm** (expectation-maximization algorithm) and **variational inference** (variational Bayes).

To make you have a clear picture, I'll also give you mathematical descriptions, with several lines of code in Python.

- [EM Algorithm](./01-gmm-em-algorithm.ipynb)
- [Variational Inference (Variational Bayesian)](02-gmm-variational-inference.ipynb)

GMM formula has summation (not multiplication) in distribution, and the log likelihood will then lead to complex expression in [maximum likelihood estimation (MLE)](https://tsmatz.wordpress.com/2017/08/30/glm-regression-logistic-poisson-gaussian-gamma-tutorial-with-r/). These methods (which approximates the optimal solutions in the repeated algorithm's steps) will address this concerns.

**EM algorithm** is based on maximum likelihood framework, but there might have several difficulties in specific cases. For instance, when some data (observation) is same as a mean value of element in GMM, it might have a singularity, in which the likelihood goes to infinity at &sigma; = 0. (This won't occur in a single Gaussian distribution.)<br>
The motivation to apply **varietional Bayesian** is to mitigate this kind of over-estimating and [over-fitting](https://tsmatz.wordpress.com/2017/09/13/overfitting-for-regression-and-deep-learning/).

With Scikit-Learn package in Python, you can use functions of both EM algorithm (```sklearn.mixture.GaussianMixture```) and variational Bayesian (```sklearn.mixture.BayesianGaussianMixture```) for GMM. However, here I'll show you implementation from scratch in Python with mathematical explanations.<br>
These ideas can also be applied to other distributions, such as, mixtures of Bernoulli distributions, etc.

> Note : See [here](https://tsmatz.wordpress.com/2017/08/30/glm-regression-logistic-poisson-gaussian-gamma-tutorial-with-r/) for the caveat of likelihood approach.
