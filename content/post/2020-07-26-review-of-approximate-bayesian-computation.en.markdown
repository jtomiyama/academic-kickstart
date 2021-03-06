---
title: Review of Approximate Bayesian Computation
author: Joshua Tomiyama
date: '2020-07-26'
slug: review-of-approximate-bayesian-computation
categories: []
tags:
  - ABC
  - Likelihood-Free Statistics
subtitle: ''
summary: ''
authors: []
lastmod: '2020-07-26T02:13:06-05:00'
featured: yes
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Recently I found a recent review of Approximate Bayesian Computation (ABC) by Mark Beaumont (whose contributions to the development of ABC are invaluable). In this post I wish to summarize his review, expand upon concepts which I personally found challenging to grasp at first, and provide my thoughts (if any) onto what directions ABC may go in. 

First off, here is the citation in the case that you would rather read it yourself than read the musings of a measly PhD student:

> Beaumont, Mark A., Approximate Bayesian Computation (March 2019). Annual Review of Statistics and Its Application, Vol. 6, Issue 1, pp. 379-403, 2019, Available at SSRN: https://ssrn.com/abstract=3382103 or http://dx.doi.org/10.1146/annurev-statistics-030718-105212

# Introduction

ABC is an alternative algorithm for obtaining a posterior sample of your parameters of interest. I will assume that you have some familiarity with Bayesian statistics and the MCMC methods typically employed to conduct the analysis. If not, then wait for a future blog post as those certainly will be a post in the future!

As for notation, we will be interested in conducting inference on the parameter-vector `\(\theta\)`. Our prior beliefs on the values of these parameters is characterized by the prior distribution `\(\pi(\theta)\)`. The vector of observations we collect from an experiment are denoted as `\(y_\text{obs}\)`.

Whereas a Gibb's sampler will require one to derive a likelihood function for the observed data and then factor that derived likelihood into the conditional distributions, ABC simply requires one to specify a model where simulations of the model are feasible. Meaning, all one needs is the ability to produce a new data set, say `\(y^*\)`, given a set of parameters `\(\theta^*\)`. The underlying hope with ABC is that parameters `\(\theta^*\)` that generate `\(y^*\)` similar or close to `\(y_\text{obs}\)` will be close to the parameters that truly generated the observed data `\(\theta\)`. 

In the case that when the generate data is **exactly** the same as the observed data, i.e. `\(y^* = y_\text{obs}\)`, then the resulting posterior distribution from ABC will be exactly the true theoretical distribution. However, in most applications producing the exact same data set is infeasible especially when the data set is rather large or if the data is continuously distributed. So instead of trying to generate exactly the same data set, one simply requires that the data produced is within some error tolerance of the observed data, i.e. `\(||y^* -y_\text{obs}|| < \epsilon\)`. 

Below is the basic rejection sampling ABC algorithm:

> Do Until N points accepted:
> 1. Draw `\(\theta_i \sim \pi(\theta)\)`
> 2. Simulate `\(x_i \sim \pi(x | \theta_i)\)` 
> 3. Reject if `\(\theta_i\)` if `\(d(S(x_i), S(y)) > \varepsilon\)`

In practice, one often uses summary statistics, `\(s_\text{obs}\)` to reduce the dimension of the data to help remedy this problem, but thi.

Because ABC does not rely on a likelihood function, it is known as a likelihood-free inference method. Naturally, this implies that it is especially useful for situations where the likelihood doesn't exist, allowing us to solve a whole new realm of problems. Even if the likelihood is derivable, there are times where it is computationally impractical to use traditional MCMC methods. For example, when one has a large dimensional latent variable - as is the case for compartmental epidemiological models - then traditional MCMC Gibbs Samplers can take **days** to converge. 
