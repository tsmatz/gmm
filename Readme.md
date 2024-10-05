# Estimate Gaussian Mixture Model (GMM) - Python Example

In this repository, I'll introduce 2 methods for Gaussian Mixture Model (GMM) estimation - **EM algorithm** (expectation-maximization algorithm) and **variational inference** (variational Bayes).<br>
To make you have a clear picture, I'll also give you mathematical descriptions, with several lines of code in Python.

- [EM Algorithm](./01-gmm-em-algorithm.ipynb)
- [Variational Inference (Variational Bayesian)](02-gmm-variational-inference.ipynb)

GMM formula has summation (not multiplication) in distribution, and the log likelihood will then lead to complex expression in regular [maximum likelihood estimation (MLE)](https://tsmatz.wordpress.com/2017/08/30/regression-in-machine-learning-math-for-beginners/). These 2 methods will then address this concern by procedural iterative algorithms (which approximate the optimal solutions).

**EM algorithm** is an iterative method based on maximum likelihood framework.<br>
This iterative algorithm is simple and light-weight compared to variational Bayesian. There might, however, have several difficulties in specific cases, because it's based on likelihood approach.<br>
For instance, when some data (observation) is exactly same as a mean of some element in GMM, it might have a singularity, in which the likelihood goes to infinity at &sigma; = 0. (This won't occur in a single Gaussian distribution.)<br>
When the number of data is insufficient, this method might also over-estimate the results.<br>
In complex system, it will be infeasible (intractable) to evaluate the posterior distribution or compute the expectation of the complete-data log likelihood with respect to the posterior distribution of the latent variables, so EM algorithm cannot be used.

In **variational Bayesian** (variational inference), we can find an approximation for the posterior distribution as well as for the model evidence.<br>
Variational Bayesian also avoids over-estimating and [over-fitting](https://tsmatz.wordpress.com/2017/09/13/overfitting-for-regression-and-deep-learning/) mentioned above, by applying Bayesian.

> Note : See [here](https://tsmatz.wordpress.com/2017/08/30/regression-in-machine-learning-math-for-beginners/) for the caveat of likelihood approach.

Here I show you the implementation from scratch in Python with mathematical explanations. But, with Scikit-Learn package in Python, you can also use functions for both EM algorithm (```sklearn.mixture.GaussianMixture```) and variational Bayesian (```sklearn.mixture.BayesianGaussianMixture```) in GMM.<br>
By knowing mathematical background and implementation, these methods can also be applied to other distributions - such as, mixtures of Bernoulli distributions, hidden Markov Models (HMM), etc. (See [here](https://github.com/tsmatz/hmm-lds-em-algorithm) for applying EM algorithms in HMM and LDS.)
