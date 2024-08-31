---
title: "Experimental Number Theory"
date : 2024-08-31T12:36:09+02:00
omit_header_text: true
short_summary: "Book published by Oxford University Press"
featured_image: "/images/frv-exp-numb-th.jpg"
no_summary: true
---

This book, published in 2007, is a discussion of various mathematical
experiments in Number Theory using the computer. The main
computational tool used is the sophisticated package
[PARI-GP](https://pari.math.u-bordeaux.fr/). Maybe the best way to
describe the book in more detail is to just quote its preface.

```
Preface
--------

 There is a long and distinguished tradition in mathematics, perhaps
 even more pronounced in number theory, whereas a chance discovery of
 a pattern or identity between numbers arising from unrelated
 calculations leads to the development of whole new fields (this is
 precisely how Gauss phrases it in a diary entry). 
 
 It is worth keeping in mind that the Birch-Swinnerton--Dyer
 conjecture, one of the million-dollar millennium problems of the Clay
 Institute, was inferred from numerical calculations.  Indeed, as
 Cassels has said, to a large degree number theory is a experimental
 science.

 The goal of this book is to introduce the reader to the use of the
 computer as a research tool in number theory. I will discuss a
 variety of different examples to illustrate what the current state of
 software and hardware allows us to compute on an everyday basis. I
 will not be concerned with the most clever possible approach to a
 given calculation or a careful analysis of the running time of a
 given algorithm. Instead, I will concentrate on what works on a small
 to medium scale: say, what can be done, from devising the algorithm,
 coding it, running it to analyzing its output, under an hour. The
 emphasis will be on the, usually short, routines we can write to
 probe a conjecture or gain insight into a problem. This kind of
 programming tends to be private, ugly and chaotic, but, when it
 works, by the end of the day we have learned something we did not
 know.
 
 I have not attempted the impossible task of being comprehensive but
 still, I have tried to cover a broad spectrum of computational
 issues. The only way I can learn how to use a new piece of software
 is by analyzing many worked out examples. That is the approach I have
 taken here. My hope is, also, that bits and pieces of the examples in
 the book could be of used for other questions you may have in mind.
 
 The main computational package I will be using is PARI-GP though I
 tried to be as little software-dependent as possible. This book,
 however, is not a PARI manual. Functions that are built-in will not
 be discussed directly; you are encouraged to look at the actual
 PARI-GP manual for their definition and usage.
 
 The book is also not an introduction to number theory though each
 chapter has a short theoretical component; I will assume you have a
 basic knowledge of the arithmetic of number fields and elliptic
 curves for example, but then again, going through some the examples
 in the book, in combination with a more standard text as a reference,
 could be of great help to learn this material.

 One last thing, I anticipate that reading this book without a
 computer at hand would be rather useless. I suggest you try the
 routines out as you read and, by all means, experiment!
```

The original page with GP
[code](https://sweet.ua.pt/apacetti/cnt-frames.html) written by the
CNT group at UT Austin ([A. Pacetti](https://sweet.ua.pt/apacetti/),
[G. Tornaría](http://www.cmat.edu.uy/~tornaria/) and myself) is now
maintained by Pacetti in Aveiro. Most, if not all, of the code
discussed in the book and more can be found in this page.

I have also started putting some GP code in my github page
[frvmath](https://github.com/frvillegas/frvmath). 



