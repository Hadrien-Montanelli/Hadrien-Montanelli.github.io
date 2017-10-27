---
layout: post
title: "Solving PDEs on the sphere"
date: 2017-10-26
---

<a href="http://arxiv.org/pdf/1701.06030.pdf">My last paper</a>, with my former colleague
<a href="http://www.opt.mist.i.u-tokyo.ac.jp/~nakatsukasa/">Yuji Nakatsukasa</a>, has just been accepted in 
<a href="http://www.siam.org/journals/sisc.php">SISC</a>. In this post, I review the main ideas of our paper. 

We are interested in computing smooth solutions of stiff PDEs on the unit sphere of the form 

$$
u_t = \Delta u + \mathcal{N}(u), \quad u(t=0,x,y,z)=u_0(x,y,z),
\label{PDE}
$$

where $$u(t,x,y,z)$$ is a function of time $$t$$ and Cartesian coordinates $$(x,y,z)$$ with $$x^2 + y^2 + z^2=1$$.
The function $$u$$ can be real or complex and the the PDE can be a single equation, as well as a system of equations.
A large number of PDEs of interest in science and engineering take this form.
Examples include the <a href="http://en.wikipedia.org/wiki/Allen–Cahn_equation">Allen--Cahn equation</a> 
$$u_t = \epsilon\Delta u + u - u^3$$, the
<a href="http://en.wikipedia.org/wiki/Nonlinear_Schrödinger_equation">nonlinear Schrödinger equation</a> 
$$u_t=i\Delta u + iu|u|^2$$, the <a href="http://en.wikipedia.org/wiki/Ginzburg–Landau_theory">Ginzburg--Landau equation</a>, and all <a href="https://en.wikipedia.org/wiki/Reaction–diffusion_system">reaction-diffusion equations</a>.

Our algorithms are based on a variant of the <a href="http://en.wikipedia.org/wiki/Double_Fourier_sphere_method">double Fourier sphere method</a> in coefficient space with multiplication matrices that differ from the usual ones, and implicit-explicit time-stepping schemes.
Operating in coefficient space with these new matrices allows one to use a sparse direct solver, avoids the coordinate singularity and maintains smoothness at the poles, while implicit-explicit schemes circumvent severe restrictions on the time-steps due to stiffness.
A comparison is made against <a href="http://en.wikipedia.org/wiki/Exponential_integrator">exponential integrators</a> 
and it is found that implicit-explicit schemes perform best.
Implementations in <a href="http://www.mathworks.com/products/matlab.html">MATLAB</a> and <a href="http://www.chebfun.org">Chebfun</a> make it possible to compute the solution of many PDEs to high accuracy in a very convenient fashion---check out the the<a href="http://www.chebfun.org/docs/guide/guide19.html"> spinsphere code</a>.

I hope to use this code for investigating <a href="http://en.wikipedia.org/wiki/Pattern_formation">pattern formation</a> on the sphere. Potential collaborators include <a href="http://www.ptrinh.com">Philippe Trinh</a>,
<a href="http://www.math.ubc.ca/~ward/">Michael Ward</a>, and <a href="http://shvartsmanlab.com">Stanislav Shvartsman</a>.
