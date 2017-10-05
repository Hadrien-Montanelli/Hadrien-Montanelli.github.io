---
layout: post
title: "The Radon transform"
date: 2017-10-05
---

Let $$f(\mathbf{x})=f(x,y)$$ be a real-valued function in $$\mathbb{R}^2$$.
The <i>Radon transform</i> of $$f$$, $$\mathcal{R}f$$, is a function defined on the space of straight lines in $$\mathbb{R}^2$$ by the line integral along each such line.

Since straight lines can be parametrized by their distance $$s$$ to the origin and the angle $$\alpha$$ that their normal vector $$\overrightarrow{n}=(\cos\alpha, \sin\alpha)$$ make with the $$x$$-axis, one can write 

$$
\begin{array}{l}
f : \mathbb{R}^2 \rightarrow \mathbb{R}, \quad
\mathcal{R}f : [0,2\pi]\times\mathbb{R} \rightarrow \mathbb{R}, \\\\
\displaystyle \mathcal{R}f(\alpha, s) = \int_{-\infty}^\infty f(x(z), y(z)) dz,
\end{array}
$$

with 

$$
x(z) = s\cos\alpha + z\sin\alpha, \quad y(z) = s\sin\alpha - z\cos\alpha.
$$

Alternatively, one could write 

$$
\mathcal{R}f(\boldsymbol{\alpha}, s) = \int_{-\infty}^\infty f(s\boldsymbol{\alpha} + z\boldsymbol{\alpha}^\perp)dz,
$$

with $$\boldsymbol{\alpha} = \overrightarrow{n} = (\cos\alpha, \sin\alpha)$$.

More generally, for $$\bold{x}\in\mathbb{R}^n$$, the Radon transform of a function $$f:\R^n\rightarrow\R$$ 
is a function defined on the space of all hyperplanes in $$\mathbb{R}^n$$.
If we parametrize these hyperplanes via $$\{\mathbf{x}\in\mathbb{R}^n \, : \, \mathbf{x}\cdot\boldsymbol{\alpha} = s\}$$ 
where $$\boldsymbol{\alpha}\in S^{n-1}$$ is a unit vector of $$\mathbb{R}^n$$ and $$s\in\mathbb{R}$$, one obtains a function defined on $$S^{n-1}\times\mathbb{R}$$ by

$$
\begin{array}{l}
f : \R^n \rightarrow \R, \quad
\mathcal{R}f : S^{n-1}\times\R \rightarrow \R, \\\\
\dsp \mathcal{R}f(\boldsymbol{\alpha}, s) 
= \int_{\bold{x}\cdot\boldsymbol{\alpha} = s} f(\bold{x}) d\bold{x}
= \int_{\boldsymbol{\alpha}^\perp} f(s\boldsymbol{\alpha} + \bold{y}) d\bold{y}.
\end{array}
$$

One has to think about $$\boldsymbol{\alpha}$$ as angles: one angle in 2D (points on the unit circle or equivalently
tangent lines to the unit circle), two angles in 3D (points on the unit sphere or equivalently tangent planes to the unit sphere), and so on.
The number $$s$$ is the (signed) distance between these hyperplanes and the origin.
