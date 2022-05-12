---
layout: post
current: post
cover: assets/images/Javadoc.png
navigation: True
title: Documentation for VStats
date: 2022-05-11 10:18:00
tags:
class: post-template
subclass: 'post'
---

Another update on VStats! 

I finally decided to make VStats a Java statistics library. After experimenting with web implementations and apps, I realized that making a library would be the most viable option for users. So, here's an update on where I'm at. 

I have all the methods ready for the initial release, so I'm currently working on writing documentation for the library using Javadoc. Writing documentation for a library is incredibly important, as it allows users of the library to understand the funcionalities of each and every method. 

For instance, here is the rendering of the documentation I wrote for a particular method (in VS Code): 

<img src="assets/images/javadocmethodtestss.png" width=700 alt="graph"/>

I've made all the methods in the VStats class <samp>static</samp>, so users can directly call the methods on the class, without having to create VStats objects. This is similar to how the Java Math library works. 

So, after I complete writing documentation for the methods I have, I will release the initial version (v$1.0$) of the library to the public. For v$1.01$, I plan to add code for $2$-sample mean and proportion confidence interval & significance test. 