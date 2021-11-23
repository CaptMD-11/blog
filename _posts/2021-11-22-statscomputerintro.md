---
layout: post
current: post
cover: assets/images/normdist4.png
navigation: True
title: Statistics Calculator Intro
date: 2021-11-22 10:18:00
tags:
class: post-template
subclass: 'post'
---


A statistical enterprise in Java... 

I recently decided to write a program that would calculate various statistics from a data set of the array data type. Since I was relatively new to both computer science and statistics, I thought it might be fun to start a project that would involve both fields. 

Using Eclipse, I was able to write the code to calculate the mean and median of a data set. 

Here is the code for the mean: 

<pre class="s-code-block language-java">
public void computeMean() {
	int sum = 0;
	double count = 0.0;
	
	for (int i = 0; i < inputData.length; i++) {
		sum = sum + inputData[i];
		count++;
	}
	// sum is calculated
	// number of elements in Array is calculated
	
	mean = sum / count;
	m_sumData = sum;
	
}
</pre>

Although there is a major error for the median code, as I have not considered the possibility that the values in the data set could be out of order, here is what I have so far: 

<pre class="s-code-block language-java">
public void computeMedian() {
	int sumIndex = 0;
	// sum of the indexes
	int middleIndex = 0;
	// average of the indexes
	
	if (inputData.length % 2 != 0) {
		middleIndex = (inputData.length / 2) + 1;
		median = inputData[middleIndex-1];
	} else {
		middleIndex =  (inputData.length / 2);
		median = ( inputData[middleIndex-1] + inputData[middleIndex] ) / 2.0;
	}
}
</pre>

I am currently working on standard deviation, which is the average distance from each data value to the mean. I also plan on adding the code for mode (the most occurring value in the data set), the remaining elements of the 5-number summary (minimum, quartiles 1 & 3, maximum), and possibly even a z-score calculator (a z-score tells you how far a value is from the mean in terms of the standard deviation, assuming a normal distribution). 

