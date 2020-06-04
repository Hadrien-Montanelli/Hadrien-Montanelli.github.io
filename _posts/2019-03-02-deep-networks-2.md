---
layout: post
title: "Deep networks and bandlimited functions"
date: 2019-03-02
---

<center><h3><i>(edited June 2020)</i></h3></center>

In a recent <a href="http://arxiv.org/pdf/1903.00735.pdf">paper</a>, my colleagues and I considered the <a href='http://en.wikipedia.org/wiki/Deep_learning'>deep</a> <a href='http://en.wikipedia.org/wiki/Rectifier_(neural_networks)'>ReLU</a> network approximation of generalized <a href='http://en.wikipedia.org/wiki/Bandlimiting'>bandlimited</a> functions $$f:B=[0,1]^d\rightarrow\mathbb{R}$$ of the form

$$
f(\boldsymbol{x}) = \int_{\mathbb{R}^d}F(\boldsymbol{w})K(\boldsymbol{w}\cdot\boldsymbol{x})d\boldsymbol{w}, \quad\mathrm{supp}\,F\subset [-M,M]^d, \quad M\geq1,
$$

for some <a href='http://en.wikipedia.org/wiki/Square-integrable_function'>square-integrable</a> function $$F:[-M,M]^d\rightarrow\mathbb{C}$$ and <a href='http://en.wikipedia.org/wiki/Analytic_function'>analytic</a> kernel $$K:\mathbb{R}\rightarrow\mathbb{C}$$.
We showed that, for any <a href='http://en.wikipedia.org/wiki/Measure_(mathematics)'>measure</a> $$\mu$$, such functions can be approximated to accuracy $$\epsilon$$ in the $$L^2(B,\mu)$$-norm by deep ReLU networks of depth $$L=\mathcal{O}\left(\log_2^2\frac{1}{\epsilon}\right)$$ and size $$W=\mathcal{O}\left(\frac{1}{\epsilon^2}\log_2^2\frac{1}{\epsilon}\right)$$, up to some constants that depend on $$F$$, $$K$$, $$\mu$$ and $$B$$.

Our theorem is based on a result by Maurey, and on the ability of deep ReLU networks to approximate <a href='https://en.wikipedia.org/wiki/Chebyshev_polynomials'>Chebyshev polynomials</a> and <a href='http://en.wikipedia.org/wiki/Analytic_function'>analytic</a> functions efficiently.

<h2>Maurey's theorem</h2>

A famous <a href='http://en.wikipedia.org/wiki/Carath%C3%A9odory%27s_theorem_(convex_hull)'>theorem</a> of <a href='http://en.wikipedia.org/wiki/Constantin_Carath%C3%A9odory'>Carath&eacute;odory</a> states that if a point $$x\in\mathbb{R}^d$$ lies in the <a href='http://en.wikipedia.org/wiki/Convex_hull'>convex hull</a> of a set $$P$$ then $$x$$ can be written as the <a href='https://en.wikipedia.org/wiki/Convex_combination'>convex combination</a> of at most $$d+1$$ points in $$P$$.
Maurey's theorem is an extension of Carath&eacute;odory's result to the infinite-dimensional case of <a href='http://en.wikipedia.org/wiki/Hilbert_space'>Hilbert spaces</a>.

<b>Theorem (Maurey).</b>
<i>Let $$H$$ be a Hilbert space with norm $$\Vert\cdot\Vert$$. 
Suppose there exists $$G\subset H$$ such that for every $$g\in G$$, $$\Vert g\Vert\leq b$$ for some $$b>0$$. 
Then, for every $$f$$ in the convex hull of $$G$$ and every integer $$n\geq 1$$, there is a $$f_n$$ in the convex hull of $$n$$ points in $$G$$ and a constant $$c>b^2-\Vert f\Vert^2$$ such that $$\Vert f - f_n\Vert^2\leq \frac{c}{n}$$.</i>

In practice, we used Maurey's theorem to show that there exists

$$
f_{\epsilon}(\boldsymbol{x}) 
= \sum_{j=1}^{\lceil 1/\epsilon^2\rceil}b_j\big[\cos(\beta_j)\mathrm{Re}(K(\boldsymbol{w}_j\cdot\boldsymbol{x})) - \sin(\beta_j)\mathrm{Im}(K(\boldsymbol{w}_j\cdot\boldsymbol{x}))\big],
\quad\sum_{j=1}^{\lceil 1/\epsilon^2\rceil}\vert b_j\vert \leq C_F,
\quad \beta_j\in\mathbb{R},
$$

such that

$$
\Vert f_{\epsilon}(\boldsymbol{x}) - f(\boldsymbol{x})\Vert_{L^2(\mu, B)}
\leq 2C_F\sqrt{\mu(B)}\epsilon.
$$

In other words, the function $$f$$ is approximated by a linear combination of analytic functions to accuracy $$2C_F\sqrt{\mu(B)}\epsilon$$ in the $$L^2(B,\mu)$$-norm. The task of approximating $$f$$ by deep ReLU networks has been reduced to approximating analytic functions by deep networks.

<h2>Chebyshev polynomials, analytic functions and deep ReLU networks</h2>

The <a href='http://en.wikipedia.org/wiki/Chebyshev_polynomials'>Chebyshev polynomials</a> of the first kind play a central role in <a href='http://en.wikipedia.org/wiki/Approximation_theory'>approximation theory</a>. They are defined on $$[-1,1]$$ via the three-term <a href='http://en.wikipedia.org/wiki/Recurrence_relation'>recurrence relation</a>

$$
T_n(x) = 2xT_{n-1}(x) - T_{n-2}(x), \quad n\geq 2,
$$

with $$T_0=1$$ and $$T_1(x) = x$$. We showed that deep ReLU networks can implement the recurrence relation efficiently. Since truncated Chebyshev series can approximate analytic functions exponentially well, so can deep networks.

