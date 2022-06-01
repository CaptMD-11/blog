---
layout: post
current: post
cover: assets/images/differentstandarddeviationsgraphs.png
navigation: True
title: Standard Deviation vs. Sample Size
date: 2022-01-16 10:18:00
tags:
class: post-template
subclass: 'post'
---

An intuitive relationship. 

Standard deviation is a statistic that simply describes how much variability (taking the data values and the mean into account) there is in a data set. Here is the formula, where <i>x</i> represents the value of interest, <i>x̄</i> represents the mean, and <i>n</i> represents the number of data values in the set (sample size): 

<img src="assets/images/standarddeviationformula.png" width=250 alt="formula"/>

Standard deviation is important as it allows you to essentially assess the level of stability in the data. To elaborate, if there is a relatively high standard deviation, then there is high variability in the data. If the standard deviation is relatively low, then there is low variability. 

For example, suppose you want to know the average number of plants per household in your country. You will consider different sample sizes of households. The first sample size of households that you take might be relatively small, so probably a few houses from your neighborhood. Let's assume that your community is pretty enthusiastic about gardening and the climate is fairly ideal. So, the average number of plants per household in your community might be drastically higher than the national average of plants per household, thus a high variability. Therefore, there is an indication of sampling bias in your community sample, since you are assessing households with similar levels of gardening enthusiasm and in the same climate. 

If you increase your sample size to households in your state or province, then you are adding more people with varying opinions on gardening and different climates, so there will be less variability when comparing the state average to the national average. Therefore, the overall bias in your sample will reduce, as the sample size increases. 

To test this out mathematically, I thought of graphing the standard deviation vs. the sample size. The problem with this is that the standard deviation formula contains two variables, <i>x</i> (which is just a data value), and <i>n</i> (which represents the sample size). In order to avoid the complexity of dealing with the 3D plane, I decided to essentially combine <i>x</i> and <i>n</i> into one variable since the domains of <i>x</i> and <i>n</i> are very similar. While <i>x</i> ∈ (-∞, +∞), <i>n</i> ∈ (1, +∞), it's evident that the domain of one of the variables must be restricted. The obvious choice was to reduce the domain of <i>x</i> to the same of that of <i>n</i>, since <i>n</i> must stay greater than 1 (you can't have a negative sample size, and you can't have a sample size of 1 since that would make the expression undefined). Therefore, my "modification" to the standard deviation function has some limitations, as it leaves out negative <i>x</i>-values, but I guess for most practical applications, this works. 

Here is my modified formula of the standard deviation, where <i>n</i> represents the sample size, and <i>S</i> represents the standard deviation function: 

<img src="assets/images/mymodstandevfunction.png" width=250 alt="formula"/>

In order to graph this, I needed to further tweak the formula. So, I set the value of <i>n̄</i> (which is the constant, <i>x̄</i>) to 1.25. I also replaced the <i>x</i> in the numerator with <i>n</i>. 

Here is the graph-ready formula: 

<img src="assets/images/graphreadystandevfunction.png" width=450 alt="formula"/>

Here is the graph of the modified formula, where sample size is on the horizontal axis (<i>n</i>-axis) and standard deviation is on the vertical axis (<i>S</i>-axis): 

<img src="assets/images/standevvssamplesizegraph.png" width=850 alt="formula"/>
<center><i>(graphed with Desmos)</i></center>
<br>

I think this visual representation shows how standard deviation and sample size are related. We see that with a relatively low sample size, there is a very high standard deviation, due to lots of potential bias. However, as we increase the sample size, the standard deviation decreases exponentially, but never reaches 0. Although the overall bias is reduced when you increase the sample size, there will always be some instances where the bias could possibly affect the stability of your distribution. This can be expressed by the following limit: 

<img src="assets/images/standevvssamplesizelimit.png" width=300 alt="formula"/>

I'd also like to mention that I used the summation of sample sizes from 1 to 100 in the formula and in the graph. Depending upon the sample size, the overall shape of this graph will be retained, as it is essentially "scaled up" or "scaled down" as you sum the (<i>n</i> - 1.25)<sup>2</sup> term in the numerator. 