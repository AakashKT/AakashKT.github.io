---
layout: post
title: Variance analysis - Stratified Sampling v/s Random sampling
date: 2023-04-27
description: Prove that variance of stratified sampling is lower as compared to random sampling.
permalink: /blog/2023/variance-stratified/
---

I was recently reading through the PBRT fourth edition, an exciting followup of the excellent <a href="https://www.pbr-book.org/3ed-2018/contents">third edition</a>. They derive & show that the variance of stratified sampling is necessarily lower than that of random sampling in Chapter 2, Sect 2.2.1 (Page 61). The derivation was not very clear to me and required some thinking/writing of my own. Plus, they refer to Eric Veach's <a href="http://graphics.stanford.edu/papers/veach_thesis/">thesis</a> for an important expression of the variance (that thesis is a gold mine!). However, I could not for the life of me find a step by step derivation of that expression there too! 

Well, that's the motivation for this blog. Writing stuff like this down helps my understanding as well :-).

<br>

Definitions
-----
We will denote random variables with capital letters like so: $$X$$. Expected value is denoted as $$E[\ ]$$ & variance is denoted as $$V[\ ]$$. 

Recall the definition of expectation: $$ E[f(X)] = \int_{D} f(x) \cdot p(x) dx$$, where $$D$$ is the domain and $$p(x)$$ is the probability of choosing $$x$$.

Also, recall that variance is expected squared deviation from mean: $$V[f(X)] = E \left [ (f(X) - E[f(X)])^2 \right ]$$.

Finally, recall that a function of a random variable is still a random variable: $$ Y = f(X) $$.

<!-- Recall that a function of a random variable is still a random variable: $$ Y = f(X) $$. -->

Let's first define our target integral over the domain $$\Lambda$$:
<p>
$$
L = \int_{\Lambda} f(x) dx.
$$
</p>
Lets now define all <b>stratum</b> $$\Lambda_1, \Lambda_2, ... \Lambda_n$$, which are non-overlapping and combine to form the whole domain: $$\bigcup_{i=1}^{n} \Lambda_i = \Lambda$$. Each stratum has fractional volume $$v_i \in (0, 1]$$.

The integral within a stratum $$i$$ is: $$L_i = \int_{\Lambda_i} f(x) dx$$.

With this, the target integral can be decomposed like so:
<p>
$$
L = \int_{\Lambda_1} f(x) dx + \int_{\Lambda_2} f(x) dx + ... + \int_{\Lambda_n} f(x) dx = \sum_i \int_{\Lambda_i} f(x) dx.
$$
</p>

We will use the following two properties of <a href="https://en.wikipedia.org/wiki/Expected_value#Properties:~:text=Linearity%20of%20expectation%3A%5B34%5D%20The%20expected%20value%20operator%20(or%20expectation%20operator)">expectation</a> and <a href="https://en.wikipedia.org/wiki/Variance#Properties:~:text=If%20all%20values%20are%20scaled%20by%20a%20constant%2C%20the%20variance%20is%20scaled%20by%20the%20square%20of%20that%20constant%3A">variance</a>, given a constant $$a$$:
<p>
$$
E[af(X)] = a E[f(X)],
$$
</p>
<p>
$$
V[af(X)] = a^2 V[f(X)]
$$
</p>

We will also use the following two properties of <a href="https://en.wikipedia.org/wiki/Expected_value#Properties:~:text=Linearity%20of%20expectation%3A%5B34%5D%20The%20expected%20value%20operator%20(or%20expectation%20operator)">expectation</a> and <a href="https://en.wikipedia.org/wiki/Variance#Properties:~:text=are-,uncorrelated,-%2C%20then%20the%20variance">variance</a>, given random variables $$X_i$$ are identically and independently distributed (as is in rendering with Monte Carlo):
<p>
$$
E \left [ \sum_i f(X_i) \right ] = \sum_i E \left [ f(X_i) \right ],
$$
</p>
<p>
$$
V \left [ \sum_i f(X_i) \right ] = \sum_i V \left [ f(X_i) \right ]
$$
</p>

Finally, we will make use of the <a href="https://en.wikipedia.org/wiki/Variance#Properties:~:text=2.-,Decomposition,-%5Bedit%5D">decomposition</a> property of variance, for two random varibles $$X, Y$$:
<p>
$$
V[X] = E \left [ V[X | Y] \right ] + V \left [ E[X | Y] \right ],
$$
</p>
which states that the variance of $$X$$ is the sum of mean of the conditional variance and the variance of the conditional mean.

<br>

Estimators
----
Using uniform sampling in the stratum $$\Lambda_i$$ with volume $$v_i$$ using $$n_i$$ samples, we can write down it's monte carlo estimator like so:
<p>
$$
F_i = \frac{1}{n_i} \sum_{j} \frac{f(X_{i, j})}{1 / v_i} = \frac{v_i}{n_i} \sum_{j} f(X_{i, j}),
$$
</p>
where $$X_{i, j}$$ is the jth sample in the ith stratum.

The estimator of the target integral can be written in terms of estimators of individual strata like so:
<p>
$$
F = \sum_i F_i.
$$
</p>

<br>

Variance of Stratified Sampling
-----
<!-- The variance within a stratum is:
<p>
$$
\sigma_i^2 = V[f(X_{i, j})] = E \left [ \left ( f(X_{i, j} - I_i) \right )^2 \right ] = \int_{\Lambda_i} (f(x) - I_i)^2 \cdot \frac{1}{v_i} dx
$$
$$
\sigma_i^2 = \frac{1}{v_i} \int_{\Lambda_i} (f(x) - I_i)^2 dx
$$
</p> -->

Denote the variance within a stratum as: $$\sigma_i^2 = V[f(X_{i, j})]$$.

Now, the vaiance of the stratum estimator $$F_i$$ is:
<p>
$$
V[F_i] = V \left [ \frac{v_i}{n_i} \sum_j f(X_{i, j}) \right ]
$$
</p>

Using the first set of properties:
<p>
$$
V[F_i] = \frac{v_i^2}{n_i^2} V \left [ \sum_j f(X_{i, j}) \right ]
$$
</p>

Using the second set of properties:
<p>
$$
V[F_i] = \frac{v_i^2}{n_i} \cdot \frac{1}{n_i} \sum_j V \left [ f(X_{i, j}) \right ]
$$
$$
V[F_i] = \frac{v_i^2}{n_i} \cdot \frac{1}{n_i} \sum_j \sigma_i^2
$$
$$
V[F_i] = \frac{v_i^2}{n_i} \cdot \sigma_i^2 \cdot \frac{1}{n_i} \sum_j 1
$$
$$
V[F_i] = \frac{v_i^2 \sigma_i^2}{n_i}
$$
</p>

Finally, the variance of the target estimator is:
<p>
$$
V[F] = V[\sum_i F_i] = \sum_i V[F_i]
$$
$$
V[F] = \sum_i \frac{v_i^2 \sigma_i^2}{n_i}
$$
</p>
Typically, we take $$n_i = v_i n$$, thus:
<p>
$$
\boxed{
V[F] = \frac{1}{n} \sum_i v_i \sigma_i^2
}
$$
</p>

<br>

Variance of Random Sampling
-----
Random sampling can be done within this framework by first choosing a stratum $$i$$ according to discrete probabilities defined by $$v_i$$ and then choosing a sample uniformly within that stratum.

Define probabilities of choosing strata like so (since $$v_i \in (0, 1]$$):
<p>
$$
p(i) = v_i,
$$
</p>
and the probability of uniformly choosing a sample $$j$$ given a stratum as:
<p>
$$
p(X_{i, j} | i) = \frac{1}{v_i}.
$$
</p>

With this, the target estimator is:
<p>
$$
F = \frac{1}{n} \sum_j \frac{f(X_{i, j})}{p(X_{i, j} | i) p(i)}
$$
$$
F = \frac{1}{n} \sum_j f(X_{i, j})
$$
</p>

<hr>
We are now choosing $$X_{i, j}$$ <b>conditionally</b> on $$I$$ (random variable on strata).

Variance of $$f(X_{i, j})$$ is not just witin a stratum like defined before.
But, we can use the <b>decomposition</b> property to get variance of $$f(X_{i, j})$$:
<p>
$$
V[f(X_{i, j})] = E \left [ V[f(X_{i, j}) | I] \right ] + V \left [ E[f(X_{i, j}) | I] \right ]
$$
</p>

<hr>
Lets look a the first term in the sum: $$ E[V[..]]$$. The variance is of $$f(X_{i, j})$$ given a stratum, which is exactly $$\sigma_i^2$$. Thus,
<p>
$$
E \left [ V[f(X_{i, j}) | I] \right ] = E[\sigma_i^2]
$$
</p>

Since expectation over strata are on discrete probabilities:
<p>
$$
E \left [ V[f(X_{i, j}) | I] \right ] = \sum_i \sigma_i^2 \cdot p(i)
$$
$$
E \left [ V[f(X_{i, j}) | I] \right ] = \sum_i \sigma_i^2 v_i
$$
</p>

<hr>
Lets now look at the second term: $$ V[E[..]]$$. Here, the expected value is of $$f(X_{i, j})$$ given a stratum, which is exactly $$L_i$$.
<p>
$$
V \left [ E[f(X_{i, j}) | I] \right ] = V[L_i]
$$
</p>

In this case, the variance will be with respect to the target integral.
<p>
$$
V \left [ E[f(X_{i, j}) | I] \right ] = E[(L_i - L)^2]
$$
</p>

Again, due to discrete probabilities:
<p>
$$
V \left [ E[f(X_{i, j}) | I] \right ] = \sum_i (L_i - L)^2 v_i
$$
</p>

<hr>
We now get an expression of the variance of $$f(X_{i, j})$$ for random sampling:
<p>
$$
V[f(X_{i, j})] = \sum_i \sigma_i^2 v_i + \sum_i (L_i - L)^2 v_i
$$
</p>

<hr>
Finally, the variance of the target estimator is:
<p>
$$
V[F] = V \left [ \frac{1}{n} \sum_j f(X_{i, j}) \right ]
$$
</p>

Again, using the first and second set of properties:
<p>
$$
V[F] = \frac{1}{n^2} \sum_j V \left [ f(X_{i, j}) \right ] = \frac{1}{n} \cdot \frac{1}{n} \sum_j V \left [ f(X_{i, j}) \right ]
$$
$$
V[F] = \frac{1}{n} V \left [ f(X_{i, j}) \right ]
$$
$$
\boxed{
V[F] = \frac{1}{n} \left [ \sum_i \sigma_i^2 v_i + \sum_i (L_i - L)^2 v_i \right ]
}
$$
</p>

<br>

Conclusion
-----
The first and the second boxed equations show the variance of stratified and random sampling respectively. Its clear that the latter's variance is larger due to the additional term.