---
layout: post
title: "Solving PDEs on the sphere"
date: 2017-10-26
---

<a href="http://arxiv.org/pdf/1701.06030.pdf">My last paper</a>, with my former colleague at Oxford
<a href="http://www.opt.mist.i.u-tokyo.ac.jp/~nakatsukasa/">Yuji Nakatsukasa</a>, has just been accepted in 
<a> href=http://www.siam.org/journals/sisc.php">SISC</a>. In this post, I review the main ideas of our paper. 

We are interested in computing smooth solutions of stiff PDEs on the unit sphere of the form 

$$
u_t = \mathcal{L}u + \mathcal{N}(u), \quad u(t=0,x,y,z)=u_0(x,y,z),
\label{PDE}
$$

where $$u(t,x,y,z)$$ is a function of time $$t$$ and Cartesian coordinates $$(x,y,z)$$ with $$x^2 + y^2 + z^2=1$$.
The function $$u$$ can be real or complex and the the PDE can be a single equation, as well as a system of equations.
In this paper, we restrict our attention to $$\mathcal{L} u = \alpha\Delta u$$ and to a nonlinear non-differential 
operator $$\mathcal{N}$$ with constant coefficients, but the techniques we present can be applied to more general cases.
A large number of PDEs of interest in science and engineering take this form.
Examples on the sphere include the (diffusive) Allen--Cahn equation $$u_t = \epsilon\Delta u + u - u^3$$, 
the (dispersive) focusing nonlinear Schr\"{o}dinger equation $$u_t=i\Delta u + iu|u|^2$$, 
the Gierer--Meinhardt, Ginzburg--Landau and Brusselator equations, and many others.

The manuscript describes in detail an algorithm for solving stiff PDEs on the sphere combining DFS method with a variety of fourth-order time-stepping schemes.  We carefully revisit the Fourier spectral method using DFS and make minor corrections to previous work, and compare different time-stepping schemes 
from a theoretical and practical viewpoint, 
to find that the IMEX-based LIRK scheme is attractive  both in efficiency and applicability. 
The manuscript also contains theoretical contributions, most notably the realness of the eigenvalues of the discretized Laplacian matrix as described in the appendix. 

<a href="http://www.chebfun.org/docs/guide/guide19.html"> spinsphere code</a>
<a href="http://www.ptrinh.com">Philippe Trinh</a>
<a href="http://www.math.ubc.ca/~ward/">Michael Ward</a> 
<a href="http://shvartsmanlab.com">Stanislav Shvartsman</a>
