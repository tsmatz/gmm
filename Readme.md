# Estimate Gaussian Mixture Model (GMM) - Python Example

In this repository, I'll introduce 2 methods for Gaussian Mixture Model (GMM) estimation - **EM algorithm** (expectation-maximization algorithm) and **variational inference** (variational Bayes).<br>
To make you have a clear picture, I'll also give you mathematical descriptions, with several lines of code in Python.

- [EM Algorithm](./01-gmm-em-algorithm.ipynb)
- [Variational Inference (Variational Bayesian)](02-gmm-variational-inference.ipynb)

GMM formula has summation (not multiplication) in distribution, and the log likelihood will then lead to complex expression in regular [maximum likelihood estimation (MLE)](https://tsmatz.wordpress.com/2017/08/30/regression-in-machine-learning-math-for-beginners/). These 2 methods will then address this concern by procedural iterative algorithms (which approximate the optimal solutions).

**EM algorithm** is based on maximum likelihood framework.<br>
For this reason, there might have several difficulties in specific cases. For instance, when some data (observation) is same as a mean value of element in GMM, it might have a singularity, in which the likelihood goes to infinity at &sigma; = 0. (This won't occur in a single Gaussian distribution.)<br>
When the number of data is insufficient, this method might also over-estimate the results.

The motivation to apply **variational Bayesian** (variational inference) is to mitigate this kind of over-estimating and [over-fitting](https://tsmatz.wordpress.com/2017/09/13/overfitting-for-regression-and-deep-learning/) by Bayesian approach.

> Note : See [here](https://tsmatz.wordpress.com/2017/08/30/regression-in-machine-learning-math-for-beginners/) for the caveat of likelihood approach.

With Scikit-Learn package in Python, you can also use functions for both EM algorithm (```sklearn.mixture.GaussianMixture```) and variational Bayesian (```sklearn.mixture.BayesianGaussianMixture```) in GMM.<br>
However, here I'll show you implementation from scratch in Python with mathematical explanations. By knowing mathematical background and implementation, these ideas can also be applied to other distributions - such as, mixtures of Bernoulli distributions, hidden Markov Models (HMM), etc. (See [here](https://github.com/tsmatz/hmm-lds-em-algorithm) for applying EM algorithms in HMM and LDS.)
