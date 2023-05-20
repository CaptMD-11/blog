---
layout: post
current: post
cover: assets/images/taylorseries_probdensityfunction.png
navigation: True
title: Taylor Series Approximation for the Normal Distribution
date: 2023-05-16 10:18:00
tags:
class: post-template
subclass: 'post'
---

An incredibly accurate and efficient method of approximating the integral of the standard normal distribution. 

For a while now, I've been thinking about finding better ways of estimating the integral of the probability density function (for the standard normal distribution), as shown below. 

$$
f(z) = \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}}
$$

I started with analyzing different types of Riemann approximations, but soon realized that it could be quite inaccuate, since by using about a ten million subintervals, the approximate would only be accurate to around $6$-$7$ decimal places. In addition, it would also be resource-intensive for an ordinary computer to execute. 

More recently, I thought about perhaps instead using a power series in order to approximate the integral. I realized that it would make sense to begin with using a Taylor series for $e^x$ centered about $0$, since the probability function is $e$-based and is symmetric about the $y$-axis. Then, I proceeded level by level in order to create a Taylor series for the probability function, as shown below. 

$$
\begin{align}
& e^z = 1 + z + \frac{z^2}{2!} + \frac{z^3}{3!} + \frac{z^4}{4!} + ... 

\\

& e^{-\frac{z^2}{2}} = 1 + \left(-\frac{z^2}{2}\right) + \frac{\left(-\frac{z^2}{2}\right)^2}{2!} + \frac{\left(-\frac{z^2}{2}\right)^3}{3!} + \frac{\left(-\frac{z^2}{2}\right)^4}{4!} + ... 

\\

& \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}} = \frac{1}{\sqrt{2\pi}} \left( 1 + \left(-\frac{z^2}{2}\right) + \frac{\left(-\frac{z^2}{2}\right)^2}{2!} + \frac{\left(-\frac{z^2}{2}\right)^3}{3!} + \frac{\left(-\frac{z^2}{2}\right)^4}{4!} + ... \right)

\\

& \hspace{2.7cm} = \frac{1}{\sqrt{2\pi}} \left(1 - \frac{z^2}{2 \cdot 1!} + \frac{z^4}{4 \cdot 2!} - \frac{z^6}{8 \cdot 3!} + \frac{z^8}{16 \cdot 4!} - ... \right)
\end{align}
$$


Now that we have the Taylor series for the probability function, we can now easily integrate this (what is essentially a) polynomial. 

$$
\begin{align}
\int \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}} dz & = \frac{1}{\sqrt{2\pi}} \left(\frac{z}{1 \cdot 1 \cdot 0!} - \frac{z^3}{3 \cdot 2 \cdot 1!} + \frac{z^5}{5 \cdot 4 \cdot 2!} - \frac{z^7}{7 \cdot 8 \cdot 3!} + \frac{z^9}{9 \cdot 16 \cdot 4!} - ... \right)

\\

& = \frac{1}{\sqrt{2\pi}} \sum_{n = 0}^{\infty} \frac{(-1)^n \cdot z^{2n+1}}{(2n+1) \cdot 2^n \cdot n!}
\end{align}
$$

Also, I found the interval of convergence for this infinite series in order to check that the approximation of the integral would apply for $z \in \mathbb{R}$, which is the domain of the probability function. The following limit confirmed this, since as $n \rightarrow \infty$, the limit goes to $0$, whose absolute value is always less than $1$. Therefore, this statement is always true, and thus the interval of convergence is $z \in (-\infty, \infty)$. 


$$
\lim_{n \rightarrow \infty} \left| \frac{(-1)^{n+1} \cdot z^{2n+3}}{(2n+3) \cdot 2^{n+1} \cdot (n+1)!} \cdot \frac{(2n+1) \cdot 2^n \cdot n!}{(-1)^n \cdot z^{2n+1}} \right|
$$

Hypothetically, if we were to find an exact value for this integral (assuming we take a definite integral), then we would need to evaluate the infinite series. We could find the exact sum for an infinite series if it was geometric or telescoping, but it doesn't appear to be the case. So, I thought of further decomposing the Taylor series for the integral of the probability function into roots by taking each term of the series and setting it equal to $\frac{\frac{d^n}{dz} \cdot z^n}{n!}$, where $n$ is the indexing value of the series. Obviously, the even values of $n$ would correspond to a $\frac{d^n}{dz}$ value of $0$, since that is the only possible numeric component of the term that could "vary."

Next, I wanted to analyze the progression of the absolute value of $\frac{d^n}{dz}$, since I already knew that we were dealing with an alternating series. Here below is a table that displays the values of the absolute value of $\frac{d^n}{dz}$ for the first $6$ odd values of $n$. 

 <table bgcolor="black">

    <tr>
        <th><center>$n$</center></th>
        <th><center>$1$</center></th>
        <th><center>$3$</center></th>
        <th><center>$5$</center></th>
        <th><center>$7$</center></th>
        <th><center>$9$</center></th>
        <th><center>$11$</center></th>
    </tr>

    <tr>
        <th><center>$\left|\frac{d^n}{dz}\right|\biggr\rvert_{z=0}$</center></th>
        <th><center>$1$</center></th>
        <th><center>$1$</center></th>
        <th><center>$3$</center></th>
        <th><center>$15$</center></th>
        <th><center>$105$</center></th>
        <th><center>$945$</center></th>
    </tr>

</table> 

Ignoring the first term, the absolute value of $\frac{d^n}{dz}$ seems to first be multiplied by $3$, then by $5$, then by $7$, and so on. I tried coming up with a sequence generator for the absolute value of $\frac{d^n}{dz}$, but it turned out to be quite challenging. After collaborating with a few students in my math class, we determined the sequence generator to be $\frac{(2n)!}{n! \cdot 2^n}$, assuming that $n$ starts at $1$. 

After substituting this into the sigma notation for the Taylor series for the integral of the probability function, here is the result: 

$$
\int \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}} dz = \frac{1}{\sqrt{2\pi}} \left(z + \sum_{n=1}^{\infty} \frac{(-1)^n \cdot z^{2n+1}}{n! \cdot 2^n \cdot (2n+1)}\right)
$$

The best part about using this series is that when we set the upper bound of the sum to just $5$, we get $12$ decimal places of accuracy. This makes for a much more efficient computation for a computer to handle, instead of using a Riemann sum of ten million subintervals. My next step is to find a way to find the exact value of the infinite series - no approximations. I'll save that for another post :) 