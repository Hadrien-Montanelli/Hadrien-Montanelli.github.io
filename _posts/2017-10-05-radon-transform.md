---
layout: post
title: "The intertwining property of the Radon transform"
date: 2017-10-05
---

My colleague <a href="http://dsrim.github.io">Donsub Rim</a> has recently written a beautiful 
<a href="http://arxiv.org/pdf/1705.03609.pdf">paper</a> about dimensional splitting for 
<a href="http://en.wikipedia.org/wiki/Hyperbolic_partial_differential_equation">hyperbolic PDEs</a>
using the 
<a href="http://en.wikipedia.org/wiki/Radon_transform#Intertwining_property">intertwining property</a> 
of the 
<a href="http://en.wikipedia.org/wiki/Radon_transform">Radon transform</a>. 
In this post, I recall the definition of the Radon transform and explain briefly the main idea of his paper.

The Radon transform $$\mathcal{R}f$$ of a function $$f:\mathbb{R}^2\rightarrow\mathbb{R}$$ is a function defined on the space of straight lines in $$\mathbb{R}^2$$ by the line integral along each such line,

$$
\begin{array}{l}
\mathcal{R}f : [0,2\pi]\times\mathbb{R} \rightarrow \mathbb{R}, \\\\
\displaystyle \mathcal{R}f(\boldsymbol{\alpha}, s) = \int_{-\infty}^\infty f(s\boldsymbol{\alpha} + z\boldsymbol{\alpha}^\perp)dz,
\end{array}
$$

where $$\boldsymbol{\alpha} = (\cos\alpha, \sin\alpha)$$ is the normal vector of the line and $$\boldsymbol{\alpha}^\perp$$ the tangent vector.

More generally, the Radon transform $$\mathcal{R}f$$ of a function $$f:\mathbb{R}^n\rightarrow\mathbb{R}$$ is a function defined on the space of all hyperplanes in $$\mathbb{R}^n$$.
If one parametrizes these hyperplanes by $$\{\mathbf{x}\in\mathbb{R}^n \, : \, \mathbf{x}\cdot\boldsymbol{\alpha} = s\}$$ 
where $$\boldsymbol{\alpha}\in S^{n-1}$$ is a unit vector of $$\mathbb{R}^n$$ and $$s\in\mathbb{R}$$, one obtains a function defined on $$S^{n-1}\times\mathbb{R}$$ by

$$
\begin{array}{l}
\mathcal{R}f : S^{n-1}\times\mathbb{R} \rightarrow \mathbb{R}, \\\\
\displaystyle \mathcal{R}f(\boldsymbol{\alpha}, s) 
= \int_{\mathbf{x}\cdot\boldsymbol{\alpha} = s} f(\mathbf{x}) d\mathbf{x}
= \int_{\boldsymbol{\alpha}^\perp} f(s\boldsymbol{\alpha} + \mathbf{y}) d\mathbf{y}.
\end{array}
$$

One has to think about $$\boldsymbol{\alpha}$$ as angles: one angle in 2D (points on the unit circle or equivalently
tangent lines to the unit circle), two angles in 3D (points on the unit sphere or equivalently tangent planes to the unit sphere), and so on.
The number $$s$$ is the (signed) distance between these hyperplanes and the origin.

The key property used by Donsub is the 
<a href="http://en.wikipedia.org/wiki/Radon_transform#Intertwining_property">intertwining property</a> 
of the Radon transform. For a function $$u:\mathbb{R}^n\rightarrow\mathbb{R}$$, 

$$
\bigg(\mathcal{R}\frac{\partial u}{\partial x_i}\bigg)(\boldsymbol{\alpha},s) 
= \alpha_i\frac{\partial}{\partial s}\Big(\mathcal{R}u(\boldsymbol{\alpha},s)\Big),
$$

i.e.,

$$
\big(\mathcal{R}\nabla u\big)(\boldsymbol{\alpha},s) 
= \boldsymbol{\alpha}\frac{\partial}{\partial s}\Big(\mathcal{R}u(\boldsymbol{\alpha},s)\Big).
$$

Using this property one can, e.g., transform a 2D transport equation

$$
u_t + \boldsymbol{\theta}\cdot\nabla u = 0, \quad \boldsymbol{\theta}\in S^1, \quad u = u(x,y,t),
$$

to a family of 1D advection equations parametrized by $$\boldsymbol{\alpha}$$,

$$
(\mathcal{R}u)_t + (\boldsymbol{\theta}\cdot\boldsymbol{\alpha})(\mathcal{R}u)_s = 0, 
\quad \mathcal{R}u = \mathcal{R}u_{\boldsymbol{\alpha}}(s,t).
$$

More generally, high-dimensional hyperbolic PDEs can be split into many 1D hyperbolic PDEs---as I said, beautiful!
