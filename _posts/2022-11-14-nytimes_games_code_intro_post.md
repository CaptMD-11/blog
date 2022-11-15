---
layout: post
current: post
cover: assets/images/nytimesgameslogo.png
#cover: assets/images/bluebackground.jpg
navigation: True
title: Solving The NY Times Games 
date: 2022-11-15 10:18:00
tags:
class: post-template
subclass: 'post'
---

A "puzzling" project. 

For around a year, I've been playing puzzles on The NY Times website. I highly recommend <a href="https://www.nytimes.com/crosswords" target="_blank">these</a> puzzles to anyone who's looking for something to challenge their mind. 

Around a week back, I began coding algorithms that could be used to solve the puzzles (particularly Letter Boxed and Spelling Bee). I've basically dedicated a class to each puzzle so that the member variables of the class stay organized (the class names are <code>LetterBoxed</code>, <code>SpellingBee</code>, etc.). Here's the <a href="https://github.com/CaptMD-11/NYTimesGames" target="_blank">link</a> to the GitHub repository if you would like to check it out. 

The objective of Letter Boxed is to make words with letters on the sides of a square, where consecutive letters cannot be from the same side. Additionally, the game gives you targets, like "try to solve in $5$ words" or "try to solve in $6$ words." Although you can solve the puzzle in those many words, I aim to solve it in $1$ or maximum $2$ words. 

However, the main challenge is to obtain a word list that contains words that match up closely with the word list that NY Times uses. For now, I'm using an Oxford English Dictionary containing $400000+$ words in a text file (<a href="https://github.com/dwyl/english-words/blob/master/words.txt" target="_blank">link</a>). If you find a better word list, please add it to the repository's GitHub <a href="https://github.com/CaptMD-11/NYTimesGames/discussions/1" target="_blank">discussion</a>. 

I'll probably make the <code>LetterBoxed</code> class into a library available on the blog pretty soon. 

The <code>SpellingBee</code> class is still in its early stages of development. 