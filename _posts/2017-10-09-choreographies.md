---
layout: post
title: "Choreographies: when planets dance"
date: 2017-10-09
---

<a href="http://arxiv.org/pdf/1505.04848.pdf">My first paper</a> as a PhD student, 
in collaboration with my friend and former colleague at Oxford 
<a href="http://scholar.google.com/citations?user=w-PVG8sAAAAJ&hl=en">Nikola Gushterov</a>, 
was about the <i>choreographies</i> of the $$n$$-body problem. 
These are very simple periodic solutions of the $$n$$-body problem, in which the bodies share a common orbit 
and are uniformly spread along it; 
see, e.g., <a href="http://www.maths.manchester.ac.uk/~jm/Choreographies/">these animations</a>.
The trivial ones are circles, and these were found by 
<a href="http://en.wikipedia.org/wiki/Joseph-Louis_Lagrange">Lagrange</a> in 1772. 
Fore more than two centuries that was the full story. 

Everything changed at the end of the 20th century, when Moore 
(<a href="http://tuvalu.santafe.edu/~moore/pubs/braids-prl.pdf">numerically in 1993</a>), 
and then Chenciner and Montgomery 
(<a href="https://arxiv.org/pdf/math/0011268.pdf">theoretically in 2000</a>), 
discovered the first non-trivial choreography: the figure-eight of the three-body problem.
And then the magic happened: in the early 2000s, Carles Simò, Professor at the University of Barcelona, found many 
<a href="http://www.math.uni-bielefeld.de/~rehmann/ECM/cdrom/3ecm/pdfs/pant3/simo.pdf">new choreographies</a> 
using numerical optimization of the so-called <i>action</i>.
In this post, I explain the idea of Simò, which coined the name <i>choreographies</i> since the $$n$$ bodies being &#34;seen to dance in a somewhat complicated way.&#34;

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
It has been well known since <a href="http://en.wikipedia.org/wiki/Henri_Poincaré">Poincaré</a> 
that the <i>principle of least action</i>, first introduced by 
<a href="https://en.wikipedia.org/wiki/Pierre_Louis_Maupertuis">Maupertuis<a/> in 1744, 
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
Since choreographies are closed curves in the complex plane, these can be represendted by <i>Fourier series</i>.
The function $$q(t)$$ becomes a function of Fourier coefficients, the action can be computed with the exponentially 
accurate trapezoidal rule, and and optimization algorithm can be used to foud the minima.

In our paper, we have recomputed the choreographies found by Simò to higher accuracy, and extended his ideas to spaces of cosntant positive curvature---check it out!
