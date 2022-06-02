---
layout: post
current: post
cover: assets/images/normdistdesmosriemannsum.png
navigation: True
title: Riemann Sums for Estimating Probabilities
date: 2022-06-02 10:18:00
tags:
class: post-template
subclass: 'post'
---

Another method of approximating an integral. 

In one of my earlier posts, I mentioned that we need to use integral calculus in order to find the area under a normal distribution. As you may recall, the formula for the normal distribution is the following, assuming $\mu=0$ and $\sigma=1$: 

$$
f(z) = \frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}}
$$

However, for functions like this taking the integral and evaluating it at $2$ bounds can be quite difficult. But, we can use another (Riemann sums) method to <i>approximate</i> the area under the function between $2$ bounds. 

I considered the $4$ different types of Riemann sums: left endpoint, right endpoint, midpoint, and trapezoidal. Left endpoint sums would result in an under approximation when the function is increasing. This would not work for all scenarios for the normal distribution, since the function is increasing for $z$-values below $0$ and decreasing for $z$-values above $0$. The same goes for right endpoint sums, since it would result in an over approximation when the function is increasing. Trapezoidal sums would result in an underestimate when the function is concave down (when the second derivative is negative), and an overestimate when the function is concave up (when the second derivative is positive). However, a midpoint Riemann sum (for any given point on this function) will result in an overestimate and an underestimate, assuming the lower/higher bound is already set. In effect, the overestimate and underestimate will cancel, thus leaving us with an midpoint sum value that is very close to the actual integral. Therefore, I used a midpoint Riemann sum in order to calculate probabilities under distributions in the VStats library. Here is the code: 

<pre class="s-code-block language-java">
public static double computeZProbMidpointRiemann(double inputZLow, double inputZHigh) {

    double sum = 0.0;

    // double increment = (inputZHigh - inputZLow)/(Math.pow(10, 7));
    double increment = 1.0 / (Math.pow(10, 7));

    for (double i = (inputZLow + (increment / 2)); i < inputZHigh; i += increment) {
        sum += (NormalPDF(i) * increment);
    }

    return sum;

}
</pre>

This method has other applications in the VStats library. For instance, I use this method in order to compute the p-value of a significance test, which allows me to make a decision regarding the null hypothesis. In the future, I will do my best to use advanced integration techniques in order to find the exact area under the normal distribution. 