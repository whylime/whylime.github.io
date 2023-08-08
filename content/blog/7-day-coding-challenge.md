---
title: 7 day coding challenge check-in ✅
description: 
date: 2023-08-07
tags: [python, coding]
---

I'm at seven days of completing at least one challenge a day on [Codewars](https://codewars.com) and it's been really enjoyable so far. Even ~10 minutes a day of doing a challenge and seeing others' solutions has been fun and helped me think through various approaches to the problems.

The little hit of dopamine when successfully solving a challenge helped me remember why I started coding in the first place, way back when I learned HTML (yes I know it's akchually a markup language and not a programming language, please get off my lawn). 

It's because it's so satisfying to write something, to build something, that exists solely because you imagined it. For me, it was (really awful) web design, with HTML hand written in Notepad, images edited in PSP7, and everything pushed directly live to my site through FileZilla (build and test locally? we didn't know her). 

The joy of seeing my desired changes reflected in my browser was like nothing I'd experienced before. The fact that this often came after rounds of troubleshooting and consulting the original StackOverflow, [lissaexplains.com](http://lissaexplains.com/), made it that much more rewarding. 

Anyway--the coding challenge. For many of the fundamental level challenges, python methods exist such that you could write a one-liner and be done. In many cases, I have. Part of the challenge has been remembering that they exist!

As a trivial example, when prompted to convert a string from lowercase to uppercase, it's useful to know that [`upper()`](https://docs.python.org/3/library/stdtypes.html#str.upper) exists. 

However, it's also been fun to go further and contemplate solutions that don't make use of obvious built-in methods. Following the previous example, you could create a dictionary to map lowercase letters to their uppercase counterparts, or you could also use `ord()` to get the ASCII value, then do a [little conversion](https://stackoverflow.com/questions/26938376/upper-case-a-full-string-without-using-upper-function-python) to produce the uppercase version. Note in both of these cases I said you could, but that doesn't mean you _should_.

This week of doing a challenge a day hasn't turned me into a 10x engineer, but it's been fun and I'm excited to continue over the next few weeks.