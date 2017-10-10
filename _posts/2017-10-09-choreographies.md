---
layout: post
title: "Choreographies: when planets dance"
date: 2017-10-09
---

<a href="http://arxiv.org/pdf/1505.04848.pdf">My first paper</a> as a PhD student, 
written with my friend and former colleague at Oxford 
<a href="http://scholar.google.com/citations?user=w-PVG8sAAAAJ&hl=en">Nikola Gushterov</a>, 
was about the <i>choreographies</i> of the $$n$$-body problem. 
These are very simple periodic solutions of the $$n$$-body problem, in which the bodies share a common orbit 
and are uniformly spread along it; 
see, e.g., <a href="http://www.maths.manchester.ac.uk/~jm/Choreographies/">these animations</a>.

Let $$z_j(t)\in\mathbb{C}$$, $$0\leq j\leq n-1$$, denote the positions of $$n$$ bodies with unit mass in the complex plane. 
The planar $$n$$-body problem describes the motion of these bodies under the action of Newton's law of gravitation, 
through the nonlinear coupled system of ODEs

$$
\displaystyle 
z_j^{''}(t) - \sum_{\underset{i\neq j}{i=0}}^{n-1} \frac{z_i(t) - z_j(t)}{\big\vert z_i(t) - z_j(t) \big\vert^3} = 0, 
\quad 0\leq j\leq n-1.
\label{newton}
$$

Since choreographies share a single orbit and are uniformly spread along it, these can be written as

$$
z_j(t) = q\Big(t + \frac{2\pi j}{n}	\Big), \quad 0\leq j\leq n-1,
\label{choreographies}
$$

for some $$2\pi$$-periodic function $$q:[0,2\pi]\rightarrow\mathbb{C}$$. 
Such solutions were named choreographies by Simò, the $$n$$ bodies being &#34;seen to dance in a somewhat complicated way.&#34;
It has been well known since Poincaré that the <i>principle of least action</i>, first introduced by Maupertuis in 1744, 
can be used to characterize choreographies: these are minima of the <i>action functional</i>, or simply <i>action</i>, 
defined as the integral over one period of the kinetic minus the potential energy,

$$
A = \int_0^{2\pi} \big(K(t) - U(t)\big)\,dt,
\label{action}
$$

with kinetic energy

$$
\displaystyle 
K(t) = \frac{1}{2}\sum_{j=0}^{n-1} \big\vert z_j'(t) \big\vert^2 = \frac{1}{2}\sum_{j=0}^{n-1} 
\Big\vert q'\Big(t + \frac{2\pi j}{n}\Big) \Big\vert^2
\label{kineticenergy}
$$

and potential energy

$$
\displaystyle 
U(t) = -\sum_{j=0}^{n-1}\sum_{i=0}^{j-1} \big\vert z_i(t) - z_j(t) \big\vert^{-1} = -\sum_{j=0}^{n-1}\sum_{i=0}^{j-1}
\Big\vert q\Big(t + \frac{2\pi i}{n}\Big) - q\Big(t + \frac{2\pi j}{n}\Big) \Big\vert^{-1}.
\label{newtonpotential}
$$

Note that the action $$A$$ depends on $$q(t)$$ via $$U(t)$$ and on $$q'(t)$$ via $$K(t)$$. 
Since the integral of $$K(t)$$ does not depend on $$j$$ and the integral of $$U(t)$$
only depends on $$i-j$$, the action functional can be rewritten

$$
\displaystyle 
A = \frac{n}{2}\int_0^{2\pi} \big\vert q'(t) \big\vert^2 dt
+ \frac{n}{2}\sum_{j=1}^{n-1} \int_0^{2\pi} \Big\vert q(t) - q\Big(t + \frac{2\pi j}{n}\Big) \Big\vert^{-1}dt.
\label{action2}
$$

Planar choreographies correspond to functions $$q(t)$$ which minimize $$A$$.

The brilliant idea of Simò (in the early 2000s) was to use numerical optimization of to find choreographies. In our paper, we recompute the choreographies found by Simò to higher accuracy, and extend his ideas to spaces of cosntant positive curvature.

Here are some pretty figures from our paper:
