---
layout: post
current: post
cover: assets/images/newchisquare.png
navigation: True
title: Implementing the Chi-Square Distribution 
date: 2022-06-07 10:18:00
tags:
class: post-template
subclass: 'post'
---

A fun learning experience! 

While writing code for the VStats Java library, I have always wanted to include some methods featuring the $\chi^2$-distribution. Unlike the $z$-distribution, the $\chi^2$-distribution is a bit more complex, such that it contains an expression that is the output of the gamma function $(\Gamma)$. 

The $\Gamma$ function is an important function in mathematics, since it allows us to compute the factorial of any real, positive number. Here is the formula: 


$$
\Gamma(x) = \frac{1}{x} \prod_{n=1}^{\infty} \left(\frac{\left(1+\frac{1}{n}\right)^x}{1+\frac{x}{n}}\right)
$$

After implementing the $\Gamma$ function in Java, the next step was to write the implementation for the $\chi^2$ function, $f$, which is as follows: 

$$
f(\chi^2) = \frac{\left(\chi^2\right)^{\frac{k}{2}-1}e^{-\frac{\chi^2}{2}}}{\left(2^{\frac{k}{2}}\right)\left(\Gamma\left(\frac{k}{2}\right)\right)}
$$

where $k$ represents the number of degrees of freedom. Here is the method I wrote for the $\Gamma$ function: 

<pre class="s-code-block language-java">
public static double computeGammaFunction(double inputZ) {
    double res = 1; 
    for (int i = 1; i <= 1000000; i++) {
        double numerator = Math.pow(1 + (1.0/i*1.0), inputZ); 
        double denominator = 1.0 + (inputZ/i*1.0); 
        res *= numerator/denominator; 
    }
    return res * (1/inputZ*1.0); 
}
</pre>

 and $\chi^2$-distribution: 

 <pre class="s-code-block language-java">
public static double computeChiSquarePDF(double chiSqrValue, int degFree) {
    if (chiSqrValue < 0)
        return 0; 
    else {
        double numerator = (Math.pow(chiSqrValue, (degFree/2.0)-1.0)) * (Math.pow(Math.E, -1.0*chiSqrValue/2.0)); 
        double denominator = (Math.pow(2, degFree/2.0)) * computeGammaFunction(degFree/2.0); 
        return numerator / denominator; 
    }
}
</pre>

Using these methods, I was able to write another method that computes the area under the $\chi^2$-distribution (using the Riemann sum approximation method which I spoke about in one of my earlier posts), which can be used to find $p$-values of statistical tests, etc. Here is the method: 

 <pre class="s-code-block language-java">
public static double computeChiSquareCDF(double lowerBound, double upperBound, int degFree) {
    double sum = 0.0; 
    double increment = (upperBound-lowerBound) / (Math.pow(10, 2)); 
    for (double i = lowerBound + (increment/2.0); i < upperBound; i+=increment) {
        sum += (increment * computeChiSquarePDF(i, degFree)); 
    }
    return sum; 
}
</pre>

The next thing I might do for VStats before I announce its first official release is write a few more methods for running statistical tests with respect to the $\chi^2$-distribution. These include the GOF test (goodness-of-fit), homogeneity test, and independence test. Hopefully the first version of VStats will be released sometime this summer! 