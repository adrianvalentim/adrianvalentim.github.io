---
author: "Adrian Valentim"
title: "[DRAFT] Master Problem Set: Real Analysis of a Single Variable"
date: "2022-01-29"
description: "Problems covering the most important subjects of real analysis of a single variable."
tags: ["mathematics", "real-analysis"]
ShowToc: true
TocOpen: true
math: true
url: /real-analysis
---

## Sequences

1. Let $a_n$ be a sequence over $R$ that converges to $L$. Is any subsequence of $a_n$ also convergent to $L$?
2. Let $a_n$ be a sequence over $R$ that converges to $L$. It is true that, for any other $M \in \mathbb{R}$, we have $|a_n - L| < |a_n - M|$, if $n$ is sufficiently large?'
3. Let $x_n \geq 0.$ If $\left(x_{n}\right) \rightarrow x$. Show that $\left(\sqrt{x_{n}}\right) \rightarrow \sqrt{x}$.
4. Squeeze Theorem: Show that if $x_{n} \leq y_{n} \leq z_{n}$ for all $n \in \mathbf{N}$, and if $\lim x_{n}=\lim z_{n}=l$, then $\lim y_{n}=l$ as well.
5. When can we say that a monotone function is necessarily convergent? Prove it!

## Limits

1. What are the most important theorems about limits of functions of a single variable?

2. Enunciate and prove the algebraic properties of limits of functions of a single variable.

3. Evaluate the following limits:
   $$
   \lim _{x \rightarrow 4} \frac{4-x}{2-\sqrt{x}} \text { and } \lim _{x \rightarrow 0} x \sin \left(\frac{1}{x}\right) .
   $$

<details>
<summary>Solution</summary>

 
The first limit is solved by noticing that $4-x = (2-\sqrt{x})(2+\sqrt{x})$  and that since $x \neq 4$ (which is always the case when considering a limit tending to $4$), we can effectuate the division being considered. 
The second follows nicely from the fact that even though $1/x \rightarrow \infty$ when $x \rightarrow 0$, the function $\sin$ is limited by 1. </details>


## Continuity

1. What intuitive notions is the definition of continuity trying to capture?

<details>
<summary>Solution</summary>


If the function $f$ is continuous at $a$, it should have the property that points close to $a$ are delivered by $f$ to points closed to $f(a)$. If we mean continuity on a given interval, we would like to function to not have dramatic jumps, that is, that a small enough movement from away from a point $x$ should result into a small movement away from $f(x).$ </details>

2. What are the most important theorems about continuity of functions of a single variable?

<details>
<summary>Solution</summary>


Equivalence between the sequential and the epsilon-delta definitions of continuity. The Annulation Theorem. The Intermediary Value Theorem. The Weierstrass Extreme Value Theorem. </details>

3. Assume $f$ and $g$ are defined on all of $\mathbf{R}$ and that $\lim _{x \rightarrow p} f(x)=q$ and $\lim _{x \rightarrow q} g(x)=r$. What condition is necessary to say that $\lim _{x \rightarrow p} g(f(x))=r$?

<details>
<summary>Solution</summary>


The function $g$ has to be continuous at $q$, since it is possible that $f(x)=q$ for some $x$ close to $p$.</details>

4. Let $f$ be a real single variable function. Prove that if $f$ is continuous at $a$ and $f(a)>0$, then there exists a $\delta>0$ such that $f(x)>0$ for any $x \in (a-\delta, a+\delta)$.

<details>
<summary>Solution</summary>


Since $f$ is continuous at $a$, take $\varepsilon$ as equal to $x$. In that way, there must be an $\delta$ such that every $x \in (a-\delta, a+\delta)$ has to be greater than zero.
</details>

## Derivatives

1. Prove that if $f$ is differentiable at a given point, then it must be also continuous at the same point.

<details>
<summary>Solution</summary>


- It follows from the algebraic properties of limits.

- Since $f$ is differentiable at a point $p$, we know that the following limit exists.
  $$
  \lim_{x \to p} \frac{f(x)-f(p)}{x-p}.
  $$
   It is evident that $\lim_{x \to p}x-p$ also exists, therefore, the its product with the limit above must also exist. Lastly, we only need to add a constant value to $\lim_{x \to p}f(x)-f(p)$ to conclude that $\lim_{x \to p}f(x)$ must also exist.
</details>

2. Prove the algebraic properties of differentiability.

<details>
<summary>Solution</summary>


The properties of sum of two functions and of sum of a function and a constant value follow trivially from the algebraic properties of limits. Multiplication and division, however, are achieved by helping ourselves with a handful of analytical subterfuge: the first, by summing zero to the upper part of the limit from the definition of derivatives; the second, by first dealing with the derivative of $1/f(x)$ using the observation that $f(x) (1/f(x))=1.$ </details>

3. Prove the Chain Rule.

<details>
<summary>Solution</summary>



- Multiplying by $1$ changes nothing. Wink. 
- To-do. </details>

2. Define what is a critical point of a function $f$. Give an example of a function for which has a critical point that is neither a maximum nor a minimum of the said function.

<details>
<summary>Solution</summary>


The critical points of a function are the points for which the derivative of the function at that point is zero. The function $f(x)=x^3$ has $0$ as a critical point, since the derivative of $x^3$ at $0$ is equal to $0$, but the function has neither maximum nor minimum points in all its domain. </details>

3. What points should be considered to find the maximum and minimum values of $f$ on a given interval?

<details>
<summary>Solution</summary>


First, the critical points of the said interval. Second, the points for which the derivative is not defined. Third, the end points of the given interval. </details>

4. If $f'(x) = 0$, for all $x$, must $f$ be a constant function?

<details>
<summary>Solution</summary>


Follows from the Mean Value Theorem. </details>

---
This problem set is still a draft. Consider subscribing to receive a short email from me once this article is complete.


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

