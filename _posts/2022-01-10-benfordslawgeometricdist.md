---
layout: post
current: post
cover: assets/images/benfordshistogram.png
navigation: True
title: Benford's Law & Geometric Distributions 
date: 2022-01-10 10:18:00
tags:
class: post-template
subclass: 'post'
---

One of the most fascinating natural phenomena! 

When I first heard about Benford's law in an episode of the Netflix series, <i>Connected: The Hidden Science of Everything</i> hosted by Latif Nasser, I was completely blown away! What amazed me most was the fact that Benford's law can be observed everywhere... and I mean EVERYWHERE! The applications of Benford's law vary from tax fraud detection to the identification of edited images. By the way, I highly recommend watching the entire series if you haven't already :) 

Benford's law essentially states that the probability of occurrences of the first digits of data values (1-9), in a relatively large data set, decreases as the value of the first digit increases. In other words, most of the numbers in a particular large data set begin with 1, the first digit with the next highest probability is 2, and so on. Here is a visual representation of Benford's law: 

<center><img src="assets/images/benfordshistogram.png" width=600 alt="histogram"/></center>

When I saw this histogram, I felt like it appeared much like a geometric distribution. A geometric distribution describes the probability that something will occur in the <i>n</i>th iteration, when given the probability of success, a binary scenario, and the independence of events. 

For example, suppose you wanted to find the probability that the first person wearing red shoes is the third person observed. This represents a geometric situation, where a randomly selected person could be wearing red shoes or not (binary), and the probability of this happening is 0.30 (assumed in this case; usually provided). We also have to make the assumption that the events are independent - that is, a person's choice of shoe color does not affect others' shoe color choices. You can use this formula to find the number of people of checked before you find one person who wears red shoes, where <i>x</i> represents number of people checked until the success occurs, <i>p</i> represents the probability of success, and <i>P</i> represents the probability function of the situation: 

<center><img src="assets/images/refinedgeometricformula.png" width=300 alt="formula"/></center>

For instance, to find the probability that the first person to wear red shoes is the third one observed, we can simply substitute our values into the formula like so: 

<center><img src="assets/images/refinedgeometricexampleformula.png" width=500 alt="formula"/></center>

Here is a histogram of a geometric distribution, just as an example: 

<center><img src="assets/images/geodisthistogram.png" width=500 alt="formula"/></center>

You might notice that this looks very similiar to the histogram of Benford's law. Well, that's because Benford's law is essentially a special case of geometric distribution. In Benford's law, the probabilities of the first numbers in a data set decrease as the starting number increases. A similar situation is seen in a geometric distribution, as the probability of the first success of an event decreases also (after a certain number of checks). The only difference that I see is that the "<i>x</i>-axis" go up to when <i>x</i> is 9, while the corresponding "<i>n</i>-axis" in a geometric distribution approaches +∞. Therefore, there is a correlation between the probability distribution in a geometric setting, compared to the Benford's law distribution. 

I wanted to see if there was a function for modeling the Benford's law distribution, and indeed there is! It's actually this logarithmic function, where I represent the leading digit of interest with <i>x</i>, and the probability of the digit with the function, <i>P</i>: 

<center><img src="assets/images/benfordslogformula.png" width=300  alt="formula"/></center>

Here is the graph of the logarithmic function (in blue), and the red shoe's example geometric function (in green): 

<center><img src="assets/images/finallogandgeodistgraphs.png" width=850  alt="formula"/></center>
<center><i>(graphed using Desmos)</i></center>
<br>

Although the graph of the geometric function does not perfectly match up with the Benford's law graph, it is a reasonably good fit, with a percent error of about 2.18%. Maybe with some further tweaking of the geometric function (in the interval <i>n</i> ∈ [0, 9]), we can model Benford's law with better accuracy. 

And this seems to make sense! As the first success is observed after a lot more checks, the probabilities of <i>x</i> decrease. The same situation is seen in the natural world, where the lack of first success detection within the beginning few checks corresponds with higher first digits. 