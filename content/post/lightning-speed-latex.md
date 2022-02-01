---
author: "Adrian Valentim"
title: "The Lightning Speed Setup for Lightning Speed LaTeX"
date: "2022-01-31"
description: "Wherein I provide a ridiculously easy to set up approach to write LaTeX as fast as your heart's desire."
tags: ["mathematics", "latex"]
ShowToc: true
TocOpen: true
math: true
---
(((THIS IS STILL A DRAFT!)))

**Objective:** To be able to write LaTeX symbols as fast as you can type.

**Time required to set up**: 10 minutes besides the time required to read the article.


Years ago I was part of a group of students who were responsible for writing solutions for the local Mathematical Olympiad practicing problems. Every single week I cursed my destiny writing every single character for every single LaTeX expression for every single function, integral, matrix, etc. Worst, in the myriad of symbols, backslashes, and dollar signs, it was easy to make silly mistakes that would inevitably come to hunt me in the near future. There must be a better way.

I had two main problems:

**Problem 1**. Typing LaTeX commands for math symbols takes too much time.

**Problem 2**. Seeing the code instead of the actual symbols can disturb the austere mathematical mind. 

**Problem 3.** You cannot just select and copy the LaTeX from resources you want to use. You have to tediously retype everything.

After a couple of months of complaining, I managed to find a solution for both problems using Emacs and a bunch of mods. I could now write mathematical theorems as fast as someone could talk. The thing is that I possibly spend more time tinkering my Emacs than I would be writing normal LaTeX for a month. While Emacs is one of the most famous and customizable text editors out there, and maybe for the power user this is still the best way to go, I would never be able to put "lightning speed setup" and Emacs on the same phrase unironically. Besides, most of you are probably using Windows, and installing Emacs and its friends on Windows can be extra troublesome. Fortunately for you, in the last year I've been using some more friendly options that, although not as sophisticated as my heavily modded and finely tuned Emacs, get the job done and done fast. 

## Solution to Problem 1: AutoHotKey is your new best friend
AutoHotKey is a free and open source software and scripting language in which you can automate all sorts of things. In this article we will be concern only with a small fraction of AutoHotKey potencial, that is, the option of setting text shortcuts.

Before I explain further, let's first convince ourselves (in case we still have any doubt) that writing LaTeX character by character is no way to live the examined life. Suppose I want to write for you about the epsilon-and-delta definition of Limits. This is what the LaTeX code would look like.

```latex
\[ \lim _{x \rightarrow x_0} f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: \\
0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon \]
```

Eventually all this code would turn to just this: 

$\lim _{x \rightarrow x_0} f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: 0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon.$ 

Too many characters to represent just a few symbols. Here is where AutoHotKey comes in. We can set key short words to give us any arbitrary number of characters. For example, when I write ```lim``` and press <kbd>TAB</kbd> it magically turns into ```\lim _{x  \rightarrow }``` with my cursor conveniently waiting right before the last curly bracket, ready for me to type the value for which $x$ is tending to. 

Some other examples:

int + <kbd>TAB</kbd>:  ```\sum_{i= }^{ } _{i}=```
sum + <kbd>TAB</kbd>:  ```\sum_{i= }^{ } _{i}=```
set + <kbd>TAB</kbd>:  ```\mathbb{ }```
imply + <kbd>TAB</kbd>:  ```\Rightarrow```
eps + <kbd>TAB</kbd>:  ```\varepsilon```

 You can go wild with those. You can set ```doc``` + <kbd>TAB</kbd> to start your whole document, import libraries, begin{document}, \maketitle and all of that. Are you writing an article and continuously repeating the same equation? Just make a shortcut for it on the fly. Are you repeatedly writing that the proof follows from the Weierstrass Theorem while not being so hot on the spelling of German of names? Just make an macro for every possible misspelling of Wieretrass (I mean, Wieerertrass) that you can possible write. The supremum of the possibilities is only your imagination.

### Setting up AHK

To start you have to go the AutoHotKey website and click on the big Download button, open the .exe file and click next until is installed. Afterwards you can right click anywhere in your desktop and see on the "New" menu the option "AutoHotKey script".  Do it. A new file will be created on your desktop, open it with Notepad or with you text editor of choice. This is where you're going to write your new shining macros.

Below I'm providing some of my shortcuts to help you begin. Copy and paste the code on the text window you just opened, deleting anything else that was already there. This language can seem a bit complicated at first, but it's intuitive and easy to pick up. I'll briefly explain some shortcuts so you can easily create your own. 

```AutoHotKey
#Hotstring C O
#Hotstring EndChars `t


::lm::$${left}

::mb::$$$${left 2} 

::frac::\frac{{}{}}{{}{}}{left 3}

::set::\mathbb{{}{}}{left 1}

::lim::\lim_{{}x \to {}}{left 1}

::imply::\Rightarrow{space}

::eps::\varepsilon
```

Hotstring is the term AutoHotKey uses to refer to those text shortcuts we were talking about. The first line ```#Hotstring C O``` sets two global settings for all the Hotstrings on this document, C and O. The former makes the abbreviations case sensitive, i.e., Lim will not serve to trigger our lim shortcut. The later tells AutoHotKey to omit the triggering key, this way we can use <kbd>Space</kbd> to trigger our shortcut without any space being actually typed in the moment. 

The second line sets the triggering key. In my script the key is <kbd>TAB</kbd> which is represented by the ``` `t ```. You can, of course, change that at will. For how to set other keys, refer to the [documentation on Hotstrings](https://www.autohotkey.com/docs/Hotstrings.htm).

Finally we come to the important part. The code here follows a simple pattern. You put the shortcut between ```::``` and the resulting text right after. Notice how the code ```::eps::\varepsilon``` means that after typing eps and pressing <kbd>TAB</kbd>, eps will be substituted by \varepsilon. We also have some special commands there. In the code ```::lm::$${left}```, {left} means that after ```lm``` is substituted by ```$$``` the cursor will moonwalk one character left, nicely stopping right where I want to write my inline math. Moreover, ```{left 3}``` is asking the script to go left three times. Reasoning by analogy, we can easily identify the purpose of ```{space}```. 

But wait, what about all those curly brackets? The thing is that curly brackets are a special use character on this scripting language, hence, if you want your script to print actual curly brackets you need to put them between curly brackets. That is, ```{{}abc{}}``` will produce ```{abc}``` as text. 

That's it. You're now prepared to start creating your own shortcuts. If you still want more, the AHK documentation have everything you'll want to know.

### Linux Alternative to AutoHotKey

AutoHotKey is a software only available for Windows. Mercifully, we have a similar option available for Linux called AutoKey which is also free and open source. You can find the repository [here](https://github.com/autokey/autokey).

## Solution to Problem 2: Obsidian,  Typora and Overleaf

### Obsidian
### Typora
### Overleaf



## Solution to Problem 3: MathPix.


## The Missing Piece: Illustrations and Graphs