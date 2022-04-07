---
layout: post
current: post
cover: assets/images/integralandchisquaredist2.png
navigation: True
title: Probability under Distributions
date: 2022-04-02 10:18:00
tags:
class: post-template
subclass: 'post'
---

Using integral calculus to calculate probabilities! 

In my post about $z$-scores & normal distributions, I briefly mentioned on how probabilities are computed using a normal distribution. In this post, I'd like to go a little more in-depth of how the calculation actually works, in addition to how this can be applied to other distributions as well. 

Let's first take the normal probability density function and write it in terms of $z$ ($z$-scores), for simplicity. We will assign the value of $\mu$ to $0$, and the value of $\sigma$ to $1$. Here is our function: 

$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}
$$

and in terms of $z$: 

$$
f(z) = \frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}}
$$

To calculate a probability, we can use calculus to integrate the normal probability density function between $2$ $z$-scores. For instance, let's assume that we select the $z$-interval from $z=-0.5$ to $z=0.5$. Here is the definite integral that we need to compute in order to find $P(-0.5 < z < 0.5)$: 

$$
P(-0.5 < z < 0.5) = \int_{-0.5}^{0.5} \frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}} \space dz
$$

The answer to this integral comes out to be about $0.38292$, which represents the probability that $z$ is between $-0.5$ and $0.5$. 

Suppose we wanted to know the probability that $z$ is between the region from $0.5$ to $+\infty$. This would be represented by the following improper integral: 

$$
P(z > 0.5) = \int_{0.5}^{+\infty} \frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}} \space dz
$$

And the answer comes out to be about $0.30854$, which is the result of integrating the normal probability density function between the two "bounds." 

What if we wanted to find a probability under, say, the $\chi^2$ distribution? We would first need to define our bounds for the integral. However, we would need to be careful with our low bound, since the minimum $\chi^2$ value for the distribution is $0$. Next, we would use the same integral calculation to calculate our probability. For this example, let's assume our degrees of freedom is equal to $4$ (for a Goodness of Fit statistical test), and our low & high bounds are $7.3$ and $+\infty$, respectively. Let $k$ represent the degrees of freedom, and $\Gamma$ represent the gamma function. Here is our integral: 

$$
P(\chi^2 > 7.3) = \int_{7.3}^{+\infty} \frac{\left(\chi^2\right)^{\frac{k}{2}-1}\cdot{e^{-\frac{\chi^2}{2}}}}{2^{\frac{k}{2}}\cdot\Gamma\left(\frac{k}{2}\right)} \space d\chi^2
$$

And, our answer turns out to be about $0.12086$. 

It's amazing that the probabilities under distributions in statistics are computed using important calculus concepts like integration. Differential calculus (as far as I know) seems to be quite rare in statistics, but we shall see what the future unfolds! 