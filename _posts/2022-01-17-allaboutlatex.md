---
layout: post
current: post
cover: assets/images/latexlogo-2.png
navigation: True
title: How I Write Mathematical Formulas
date: 2022-01-17 10:18:00
tags:
class: post-template
subclass: 'post'
---

Why I use $\rm\LaTeX$! 

If you've seen some of my previous posts about different concepts in statistics, I provide mathematical formulas to illustrate certain ideas. I use a software called $\rm\LaTeX$, which allows me to accomplish this by writing some basic code. 

I actually use <a href="https://artofproblemsolving.com/texer" target="_blank">this</a> neat online $\rm\LaTeX$ editor, which allows me to directly copy over the output formula to my computer. 

For instance, suppose I wanted to write the probability density function, as shown here: 

<img src="assets/images/newprobdensityfunction.png" width=300 alt="formula"/>
 
All I have to do is write the code that will generate the formula, and I'm done! Here is the code itself: 

<pre>\begin{displaymath}
f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}
\end{displaymath}</pre>

$\rm\LaTeX$ can also be used to write formal research papers and even textbooks.

The syntax for the $\rm\LaTeX$ language is very simple & intuitive, which makes it very easy for people to learn. Thus, I would highly recommend this software, even if you are new to writing code. Here is the download <a href="https://www.latex-project.org/get/" target="_blank">link</a> to install on your computer if you're interested. 