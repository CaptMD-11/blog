---
layout: post
current: post
cover: assets/images/editednewgithublogo.png
navigation: True
title: VStats GitHub Repository
date: 2022-02-26 10:18:00
tags:
class: post-template
subclass: 'post'
---

A home for the code in the cloud. 

Over the past few weeks, I have been adding many Java classes to the VStats project. These classes include calculations for confidence intervals, significance tests, linear regression, sample proportions, and more. It has been an incredibly fun experience, as I have used a multitude of data structures. My plan is to continue writing code, which will further diversify the statistical functions included in the project. I still need to work on optimizing the code, however, so that the programs will run in the most efficient manner possible. 

For fun, I wanted to share some code I wrote for computing probabilities under the standard normal distribution: 

<pre class="s-code-block language-java">
public double computeFiniteZProbMidpointRiemann(double inputZLow, double inputZHigh) {
		
	double sum = 0.0;
		
	double increment = (inputZHigh - inputZLow)/(Math.pow(10, 7)); 
		
	for (double i = (inputZLow + (increment/2)); i < inputZHigh; i+= increment) {
		sum += (NormalPDF(i) * increment); 
	}
		
	return sum; 
		
}
</pre>

In order to make the code available to the public, I have created a repository on GitHub, which contains all the classes and a short README, which describes what the project is about. Here is a <a href="https://github.com/CaptMD-11/VStats" target="_blank">link</a> to the repository, in case you're interested :) 

I am also considering making an application instead of a website for VStats, so that users will still have access to all the functions, regardless of internet status. 