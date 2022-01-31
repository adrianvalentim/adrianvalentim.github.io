---
author: "Adrian Valentim"
title: "The Lightning Speed Setup for Lightning Speed LaTeX"
date: "2022-01-31"
description: "My LaTeX setup."
tags: ["mathematics", "latex"]
ShowToc: true
TocOpen: true
math: true
---
**THIS IS STILL A DRAFT!**

*Wherein I provide a ridiculously easy to set up approach to write LaTeX as fast as your heart's desire.* 



**Objective:** To be able to write LaTeX symbols as fast as you can type.

**Time required to set up**: 5 minutes besides the time required to read the article.


Years ago I was part of a group of students who were responsible for writing solutions for the local Mathematical Olympiad practicing problems. Every single week I cursed my destiny writing every single character for every single LaTeX expression for every single function, integral, matrix, etc. Worst, in the myriad of symbols, backslashes, and dollar signs, it was easy to make silly mistakes that would inevitably come to hunt me in the near future. There must be a better way.

I had two main problems:

Problem 1. Typing LaTeX commands for math symbols takes too much time.

Problem 2. Seeing the code instead of the actual symbols can disturb the austere mathematical mind. 

After a couple of months of complaining, I managed to find a solution for both problems using Emacs and a bunch of mods. I could now write mathematical theorems as fast as someone could talk. The thing is that I possibly spend more time tinkering my Emacs than I would be writing normal LaTeX for a month. While Emacs is one of the most famous and customizable text editors out there, and maybe for the power user this is still the best way to go, I would never be able to put "lightning speed setup" and Emacs on the same phrase unironically. Besides, most of you are probably using Windows, and installing Emacs and its friends on Windows can be extra troublesome. Fortunately for you, in the last year I've been using some more friendly options that, although not as sophisticated as my heavily modded and finely tuned Emacs, get the job done and done fast. 

## Problem 1. AutoHotKey is your new best friend
AutoHotKEy is a macro bla bla bal.

Before I explain further, let's first convince ourselves (in case we still have any doubt) that writing LaTeX character by character is no way to live the examined life. Suppose I want to write for you about the epsilon-and-delta definition of Limits. This is what the LaTeX code would look like.

```latex
\[ \lim _{x \rightarrow x_0} f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: \\
0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon \]
```

Eventually all this code would turn to just this: 

$\lim _{x \rightarrow x_0} f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: \\ 0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon.$ 

Too many characters to represent just a few symbols. 