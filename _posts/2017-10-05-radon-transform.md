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
f : \R^2 \rightarrow \R, \quad
\mathcal{R}f : [0,2\pi]\times\R \rightarrow \R, \\\\
\dsp \mathcal{R}f(\alpha, s) = \int_{-\infty}^\infty f(x(z), y(z)) dz,
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
