---
layout: post
title: "Solving nonlocal PDEs on the sphere"
date: 2018-01-25
---

<div style="text-align: center;">
	<img src="/blog/nonlocalpdesphere.jpg" style="width:660px;height:287px;">
</div>

I have just submitted <a href="http://arxiv.org/pdf/1801.04902.pdf">a paper</a> 
about <a href="http://www.ma.utexas.edu/mediawiki/index.php/Introduction_to_nonlocal_equations">nonlocal PDEs</a> 
on the sphere with my colleagues 
<a href="http://home.cc.umanitoba.ca/~slevinrm/">Mikael Slevinsky</a> and 
<a href="http://www.columbia.edu/~qd2125/">Qiang Du</a>. 
Here are the main ideas of our work.

We proposed a fast <a href="http://en.wikipedia.org/wiki/Spectral_method">spectral method</a> 
for computing solutions of nonlocal models of the form

$$
u_t = \epsilon^2\mathcal{L}_\delta u + \mathcal{N}(u), \quad u(t=0,\mathbf{x}) = u_0(\mathbf{x}), \quad \epsilon>0,
$$

where $$u(t,\mathbf{x})$$ is a function of time $$t\ge0$$ and position $$\mathbf{x}$$ 
on the unit sphere $$\mathbb{S}^2\subset\mathbb{R}^3$$,
$$\mathcal{N}$$ is a nonlinear operator with constant coefficients (e.g., $$\mathcal{N}(u)=u-u^3$$), 
and $$\mathcal{L}_{\delta}$$ is a nonlocal 
<a href="http://en.wikipedia.org/wiki/Laplace%E2%80%93Beltrami_operator">Laplace--Beltrami operator</a>,

$$
\mathcal{L}_\delta u(\mathbf{x}) = \int_{\mathbb{S}^2} \rho_\delta(\vert\mathbf{x}-\mathbf{y}\vert)
[u(\mathbf{y}) - u(\mathbf{x})]\,d\Omega(\mathbf{y}).
$$

In the definition above, $$d\Omega(\mathbf{y})$$ denotes the standard 
<a href="http://en.wikipedia.org/wiki/Measure_(mathematics)">measure</a> on 
$$\mathbb{S}^2$$ and $$\rho_\delta$$ is a suitably defined nonlocal kernel with 
horizon $$0<\delta\le2$$, which determines the range of interactions. 

There has been substantial work on the numerical approximation of this type of equations in 
<a href="http://en.wikipedia.org/wiki/Euclidean_geometry">Euclidean geometries</a>.
However, no study has been attempted so far to investigate similar 
<a href="http://en.wikipedia.org/wiki/Discretization">discretizations</a> on the sphere. 
It is of practical interests to study the extension to 
<a href="http://en.wikipedia.org/wiki/Non-Euclidean_geometry">non-Euclidean geometries</a> 
(the sphere being a representative example) for the modelling of 
<a href="http://en.wikipedia.org/wiki/Anomalous_diffusion">anomalous diffusion</a>, 
<a href="http://en.wikipedia.org/wiki/Pattern_formation">pattern formation</a> 
and <a href="http://en.wikipedia.org/wiki/Image_analysis">image analysis</a>.

Our algorithms are based on the diagonalizability of nonlocal diffusion operators in the basis of 
<a href="http://en.wikipedia.org/wiki/Spherical_harmonics">spherical harmonics</a>, 
the computation of their <a href="http://en.wikipedia.org/wiki/Eigenvalues_and_eigenvectors">eigenvalues</a> 
to high relative accuracy using <a href="http://en.wikipedia.org/wiki/Numerical_integration">quadrature</a> 
and <a href="http://en.wikipedia.org/wiki/Asymptotic_analysis">asymptotic formulas</a>, 
and a fast spherical harmonic transform.
The picture at the top shows the numerical solutions of the local (first row) 
and nonlocal (second row) 
<a href="https://en.wikipedia.org/wiki/Allen%E2%80%93Cahn_equation">Allen--Cahn</a> equation.
If you want to konw more about our algorithms, check our paper out!