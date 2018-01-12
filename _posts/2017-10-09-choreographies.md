---
layout: post
title: "Choreographies: when planets dance"
date: 2017-10-09
---

<div style="text-align: center;">
	<img src="/blog/choreo.jpg" style="width:733px;height:231px;">
</div>

<a href="http://epubs.siam.org/doi/abs/10.1137/15M1024652">My second paper</a> as a PhD student, 
in collaboration with my friend and former colleague at Oxford 
<a href="http://scholar.google.com/citations?user=w-PVG8sAAAAJ&hl=en">Nikola Gushterov</a>, 
was about the <a href="http://www.scholarpedia.org/article/N-body_choreographies">choreographies</a> 
of the <a href="http://en.wikipedia.org/wiki/N-body_problem">$$n$$-body problem</a>. 
These are very simple periodic solutions of the $$n$$-body problem, in which the bodies share a common orbit and are uniformly spread along it; see, e.g., <a href="http://www.maths.manchester.ac.uk/~jm/Choreographies/">these animations</a>.
The trivial ones are circles, and these were found by 
<a href="http://en.wikipedia.org/wiki/Joseph-Louis_Lagrange">Lagrange</a> in 1772. 
Fore more than two centuries, this was the full story. 
Everything changed at the end of the 20th century, when <a href="http://tuvalu.santafe.edu/~moore/pubs/braids-prl.pdf">Moore
</a> (numerically in 1993), 
and <a href="https://arxiv.org/pdf/math/0011268.pdf">Chenciner and Montgomery</a> (theoretically in 2000), 
discovered the first non-trivial choreography: the 
<a href="https://arxiv.org/pdf/math/0011268.pdf">figure-eight</a> of the three-body problem.
And then the magic happened: in the early 2000s, 
<a href="http://www.math.uni-bielefeld.de/~rehmann/ECM/cdrom/3ecm/pdfs/pant3/simo.pdf">Simò</a> found many 
new choreographies using <a href="http://en.wikipedia.org/wiki/Mathematical_optimization">numerical optimization</a> of the so-called <a href="http://en.wikipedia.org/wiki/Action_(physics)">action</a>.
In this post, I explain the idea of Simò, who coined the term choreographies, the $$n$$ bodies being &#34;seen to dance in a somewhat complicated way.&#34;

Let $$z_j(t)\in\mathbb{C}$$, $$0\leq j\leq n-1$$, denote the positions of $$n$$ bodies with unit mass in the complex plane. 
The $$n$$-body problem describes the motion of these bodies under the action of 
<a href="http://en.wikipedia.org/wiki/Newton%27s_law_of_universal_gravitation">Newton's law of gravitation</a>, through the nonlinear coupled system of ODEs

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
that the <a href="http://en.wikipedia.org/wiki/Principle_of_least_action">principle of least action</a>, first introduced by 
<a href="http://en.wikipedia.org/wiki/Pierre_Louis_Maupertuis">Maupertuis<a/> in 1744, can be used to characterize choreographies: these are minima of the action, defined as the integral over one period of the 
<a href="http://en.wikipedia.org/wiki/Kinetic_energy">kinetic</a> minus the 
<a href="http://en.wikipedia.org/wiki/Potential_energy">potential</a> energy,

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
only depends on $$i-j$$, the action can be rewritten

$$
\displaystyle 
A = \frac{n}{2}\int_0^{2\pi} \big\vert q'(t) \big\vert^2 dt
+ \frac{n}{2}\sum_{j=1}^{n-1} \int_0^{2\pi} \Big\vert q(t) - q\Big(t + \frac{2\pi j}{n}\Big) \Big\vert^{-1}dt.
\label{action2}
$$

Choreographies correspond to functions $$q(t)$$ which minimize $$A$$. Since these are closed curves in the complex plane, these can be represendted by 
<a href="http://en.wikipedia.org/wiki/Fourier_series">Fourier series</a>.
The action $$A$$ becomes a function of Fourier coefficients, can be computed with the
<a href="http://people.maths.ox.ac.uk/trefethen/publication/PDF/2014_149.pdf">exponentially accurate trapezoidal rule</a>, 
and an optimization algorithm (over a finite number of Fourier coefficients) can be used to found the minima.

In our paper, we have recomputed the choreographies found by Simò to higher accuracy, and extended his work to spaces of cosntant positive curvature---check it out!
