---
author: "Adrian Valentim"
title: "The Lightning Speed Setup for Lightning Speed LaTeX"
date: "2022-02-01"
description: "Wherein I provide a ridiculously easy to set up approach to write LaTeX as fast as your heart's desire."
tags: ["mathematics", "latex"]
ShowToc: true
TocOpen: true
math: true
url: /speed-latex
---

## Defining the problems

**Objective:** To be able to write LaTeX symbols as fast as you can type.

**Time required to set up**: 10 minutes besides the time required to read the article.


Years ago I was part of a group of students who were responsible for writing solutions for the local Mathematical Olympiad practicing problems. Every single week I cursed my destiny writing every single character for every single LaTeX expression for every single function, integral, matrix, etc. Worst, in the myriad of symbols, backslashes, and dollar signs, it was easy to make silly mistakes that would inevitably come to hunt me in the near future.

Another common source of grief was having to retype the LaTeX for a particular problem we choose from a PDF or book. Short of emailing the author, there was no way to get the source code for a math expression. Please, not the 3x3 Matrix again.

To summarize, I had three main problems:

**Problem 1**. Typing LaTeX commands for math symbols takes too much time.

**Problem 2**. Seeing the code instead of the actual symbols can disturb the austere mathematical mind.

**Problem 3.** You cannot just select and copy the LaTeX from the resources you want to use. You have to tediously retype everything.

After a couple of months of complaining, I managed to find a solution for the first two problems using Emacs and a bunch of mods. I could now write mathematical theorems as fast as someone could talk. The thing is that I possibly spend more time tinkering my Emacs than I would be writing normal LaTeX for a month.

While Emacs is one of the most famous and customizable text editors out there, and maybe for the power user this is still the best way to go, I would never be able to put "lightning speed setup" and Emacs on the same phrase unironically. Besides, most of you are probably using Windows, and installing Emacs and its friends on Windows can be extra troublesome. Fortunately for you, in the last year I've been using some more friendly options that, although not as sophisticated as my heavily modded and finely tuned Emacs, get the job done and done fast.

## Solution to Problem 1: AutoHotKey is your new best friend
AutoHotKey is free and open-source software and scripting language in which you can automate all sorts of things. In this article, we will be concerned only with a small fraction of AutoHotKey potential, that is, the option of setting text shortcuts.

Before I explain further, let's first convince ourselves (in case we still have any doubt) that writing LaTeX character by character is no way to live the examined life. Suppose I want to write for you about the epsilon-and-delta definition of Limits. This is what the LaTeX code would look like:

```latex
\lim _{x \rightarrow x_0} f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: \\
0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon
```

Eventually all this code would turn to just this:

$ \lim_{x \rightarrow x_0}f(x)=L \iff \forall \varepsilon > 0 , \exists \delta >0: 0<\left|x-x_{0}\right|<\delta \Longrightarrow|f(x)-L|<\varepsilon.$

Too many characters to represent just a few symbols. Here is where AutoHotKey comes in. We can set key short words to give us any arbitrary number of characters. For example, when I write ```lim``` and press <kbd>TAB</kbd> it magically turns into ```\lim _{x  \rightarrow }``` with my cursor conveniently waiting right before the last curly bracket, ready for me to type the value for which $x$ is tending to.

Some other examples:

int + <kbd>TAB</kbd>:  ```\sum_{i= }^{ } _{i}=```  
sum + <kbd>TAB</kbd>:  ```\sum_{i= }^{ } _{i}=```  
set + <kbd>TAB</kbd>:  ```\mathbb{ }```  
imply + <kbd>TAB</kbd>:  ```\Rightarrow```  
eps + <kbd>TAB</kbd>:  ```\varepsilon```  

You can go wild with those. You can set ```doc``` + <kbd>TAB</kbd> to start your whole document, import libraries, begin{document}, \maketitle and all of that. Are you writing an article and continuously repeating the same equation? Just make a shortcut for it on the fly. Are you repeatedly writing that the proof follows from the Weierstrass Theorem while not being so hot on the spelling of German of names? Just make a macro for every possible misspelling of Wieretrass (I mean, Wieerertrass) that you can possibly write. The supremum of the possibilities is only your imagination.

### Setting up AHK

To start, go to the [AutoHotKey website](https://www.autohotkey.com/) and click on the big download button, open the .exe file and click next until is installed. Afterward, you can right-click anywhere on your desktop and see on the "New" menu the option "AutoHotKey script".  Do it. A new file will be created on your desktop, open it with Notepad or with your text editor of choice. This is where you're going to write your new shining macros.

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

::int:: \int \, dx{left 5}

::dint:: \int_{a}^{b}  \, dx{left 5}
```

Hotstring is the term AutoHotKey uses to refer to those text shortcuts we were talking about. The first line ```#Hotstring C O``` sets two global settings for all the Hotstrings on this document, C and O. The former makes the abbreviations case sensitive, i.e., Lim will not serve to trigger our lim shortcut. The latter tells AutoHotKey to omit the triggering key, this way we can use <kbd>Space</kbd> to trigger our shortcut without any space being actually typed in the moment.

The second line sets the triggering key. In my script the key is <kbd>TAB</kbd> which is represented by the ``` `t ```. You can, of course, change that at will. For how to set other keys, refer to the [documentation on Hotstrings](https://www.autohotkey.com/docs/Hotstrings.htm).

Finally, we come to the important part. The code here follows a simple pattern. You put the shortcut between ```::``` and the resulting text right after. Notice how the code ```::eps::\varepsilon``` means that after typing eps and pressing <kbd>TAB</kbd>, eps will be substituted by \varepsilon. We also have some special commands there. In the code ```::lm::$${left}```, {left} means that after ```lm``` is substituted by ```$$``` the cursor will moonwalk one character left, nicely stopping right where I want to write my inline math. Moreover, ```{left 3}``` is asking the script to go left three times. Reasoning by analogy, we can easily identify the purpose of ```{space}```.

But wait, what about all those curly brackets? The thing is that curly brackets are a special use character on this scripting language, hence, if you want your script to print actual curly brackets you need to put them between curly brackets. That is, ```{{}abc{}}``` will produce ```{abc}``` as text.

That's it. You're now prepared to start creating your own shortcuts. If you still want more, the AHK documentation has everything you'll want to know.

### Linux Alternative to AutoHotKey

AutoHotKey is a software only available for Windows. Mercifully, we have a similar option available for Linux called AutoKey which is also free and open source. You can find the repository [here](https://github.com/autokey/autokey).

## Solution to Problem 2: Three different options

Remember that what we want here is to be able to see the rendered LaTeX expression right on our text editor as we type. Trust me, it makes all the difference. Nowadays I sometimes think about problems and theorems writing directly in LaTeX, something I would never comfortably do if I was seeing the code `\int_{a}^{b} f(x) \, dx` instead of the beautiful squiggly curves of the integral sign.

There are many plugins for famous text editors that try to do this with varying rates of success, but I'll instead present three options that come ready to work without any tinkering.

### Obsidian

Obsidian is a free knowledge base software and markdown text editor. As was the case with AutoHotKey, Obsidian has many other powerful use cases other than the LaTeX rendering we want.

To start you just head to the [Obsidian website](https://obsidian.md/) and download the newest version. Obsidian is available on Windows, MacOS, and Linux. Next, next, install. Open Obsidian and click to create a new Vault -- this is where Obsidian will store your markdown files. Go to Settings > Editor > Default Editing Mode and make sure that the "Live Preview" option is selected. Now just create a new file and it's math time.

If plan to write personal notes, it will be difficult to find an option better than Obsidian. You have many theme options, community plugins, and custom options. You can create internal links between your notes and navigate through a graph view. You can also quickly export any file as a PDF.

If, however, you are writing an article that needs to become a standard LaTeX PDF, you can just select, copy and paste your code to your favorite application and quickly adapt it there. There is even a community plugin to make the whole process easier by automatically changing the titles, subtitles, etc., to usual the usual LaTeX code. To install it just go to Settings > Community Plugins > Browse and search "Copy as Latex".

### Typora

Typora is a minimalist and elegant markdown editor. You just open a file, select your theme and start writing. No distractions. Typora will automatically render the LaTeX as you write your math between dollars signs. There are a couple of official themes (and many community ones) to select from, and almost all of them are beautiful. You can export your files as LaTeX code or directly as a PDF.

It's very difficult to beat Typora on the user-experience side of writing a single file. Differently from Obsidian, though, Typora doesn't help you manage or link your files. Also, Typora is not free anymore, and it costs (at the time of writing) one payment of 15 dollars. To download, head to the [Typora website](https://typora.io/) and follow the arrows.

### Overleaf

You probably already know this one, so I'll be brief. Overleaf is an online text editor created specifically for LaTeX files. It's free for personal use but has many subscription options for extended features.

Open the [Overleaf website](https://www.overleaf.com/), create an account, and open a new file. You'll see a Rich Text option above your editor. Using it, most of your math symbols will be rendered inline. It doesn't work for all LaTeX expressions you may type, and in this case, you'll see the code as you normally would.

If you want to write an assignment, test, or anything that needs to be on your preferred LaTeX template, just using Overleaf is your best option. It also has features for online collaboration (although collaboration with more than one person is not available for free). However, it's not ideal to manage your notes and files, Obsidian would be more suitable in this case. Nor it's the most simple and user-friendly option, that title would go to Typora.

## Solution to Problem 3: Thank you for existing, MathPix.

MathPix is a free image recognizing and file converter software made for math expressions. Using it you can convert any PDF or image file directly to LaTeX. Or even better, you can select any particular expression on your screen instantly convert it to LaTeX.

Want to copy a part of the PDF you're reading to your personal notes? Just press <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>M</kbd> and select the part you want. Do you want to scavenge a problem from an old book physical and give it to your students? Install the mobile app on your phone and just scan it with your phone. Tell me if that's not the most beautiful thing you read today.

To finally feel true happiness, head to the [MathPix website](https://mathpix.com/), create your free account, and download for your OS of choice. Alternatively, you can find the app wherever you usually go to download them. Now go convert some images.

## The Missing Piece: Illustrations and Graphs

It's just a matter of getting used to the shortcuts before you start writing mathematics faster in LaTeX than you would on paper. Still, what about the illustrations, diagrams, graphs, and scribbles you can easily draw on your paper notes? There are fast ways to make the process of creating an image and adding it in PDF format to your notes. It's just that I don't have any tools to make the setup process fast. The method I use takes time to tinker with, but the result is worth it.

A couple of years ago, there was a post about how a math student took notes on classes using LaTeX all through his undergraduate studies that went viral on the internet. Even some groups at my University were talking about it. The setup used Vim and some mods to make something equivalent to what I used to do with Emacs. His workflow admittedly looked better although it was harder to set up. However, what really impressed me about the way he took notes was his process for creating mathematical illustrations fast. Really fast. And how beautiful they all looked.

[Here is the link](https://castel.dev/post/lecture-notes-2/) for his article. Although his method assumes you're using Vim, adapting it using AutoHotKey and any of the above text editors is possible, and the best option for quick illustrations that I know of. I may come back to this point at another time and expand the steps to make such an adaptation.

## Final Thoughts

Sometimes I get the urge to knock on every door of my university's mathematics department and tell this gospel to every math professor I can find. The amount of time you can save by using a setup like this is palpable. It's more time to think, to prove, and to write. But it's not just about time. Imagine if every mathematician wrote more of their personal notes on LaTeX instead of paper. Imagine having some of those notes available on the internet. How cool would that be?

This simple setup also turns LaTeX more accessible. You don't need to remember or google every symbol anymore. You just need to remember your shortcut. Maybe that's the final push someone needed to start writing their thoughts on mathematics or science for the world to see. Maybe that someone is you.

---

If you think that this article may be useful to someone else, you can easily share it on social media by using the buttons below. If you particularly liked it, consider [buying me a coffee](https://www.buymeacoffee.com/adrianvalentim) or subscribing for free to receive an email when I publish a new article!

<!-- Begin Mailchimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/horizontal-slim-10_7_dtp.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; width:100%;}
	/* Add your own Mailchimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="https://computer.us14.list-manage.com/subscribe/post?u=29d0fb992faa536cc7e5a2e6a&amp;id=8a7886b847" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	<label for="mce-EMAIL">Subscribe</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_29d0fb992faa536cc7e5a2e6a_8a7886b847" tabindex="-1" value=""></div>
        <div class="clear foot">
           <input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button">
        </div>
	<p><a href="http://eepurl.com/hTHzsb" title="Mailchimp - email marketing made easy and fun"><img class="referralBadge" src="https://eep.io/mc-cdn-images/template_images/branding_logo_text_dark_dtp.svg"></a></p>
    </div>
</form>
</div>

<!--End mc_embed_signup-->
