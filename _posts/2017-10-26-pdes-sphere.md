---
layout: post
title: "Solving PDEs on the sphere"
date: 2017-10-26
---

<a href="http://arxiv.org/pdf/1701.06030.pdf">My last paper</a>, with my former colleague at Oxford
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

We have designed algorithms for solving such PDEs with spectral accuracy in space and fourth-order accuracy in time.
These are based on a variant of the double Fourier sphere method in coefficient space with multiplication matrices that differ from the usual ones, and implicit-explicit time-stepping schemes.
Operating in coefficient space with these new matrices allows one to use a sparse direct solver, avoids the coordinate singularity and maintains smoothness at the poles, while implicit-explicit schemes circumvent severe restrictions on the time-steps due to stiffness.
A comparison is made against exponential integrators and it is found that implicit-explicit schemes perform best.
Implementations in MATLAB and Chebfun make it possible to compute the solution of many PDEs to high accuracy in a very convenient fashion.

There are several methods to discretize the spatial part of the PDE with spectral accuracy,
including spherical harmonics, radial basis functions and the double Fourier sphere (DFS) method.
The DFS method is the only one that leads to a $$\mathcal{O}(N\log N)$$ complexity per time-step, where $$N$$ is the total number of grid points in the spatial discretization.
We have presented in the paper a novel formulation operating in coefficient space.

Once the spatial part of \reff{PDE} has been discretized by the DFS method on an $n\times m$ uniform longitude-latitude grid, it becomes a system of $nm$ ODEs,
\begin{equation} 
\hat{u}' = \mathbf{L}\hat{u} + \mathbf{N}(\hat{u}), \quad \hat{u}(0)=\hat{u}_0,
\label{ODE}
\end{equation}

\noindent where $\hat{u}(t)$ is a vector of $nm$ Fourier coefficients and $\Lbf$ (an $nm\times nm$ matrix) and $\Nbf$ are the discretized versions of $\mathcal{L}$ and $\mathcal{N}$ in Fourier space. Solving the system \reff{ODE} with generic explicit time-stepping schemes can be highly challenging because of \textit{stiffness}:
the large eigenvalues of $\Lbf$---due to the second differentiation order in \reff{PDE} and the clustering of points near the poles---force one to use very small time-steps. 
Exponential integrators and implicit-explicit (IMEX) schemes are two classes of numerical methods that are aimed at treating stiffness.
For exponential integrators, the linear part~$\Lbf$ is integrated exactly using the matrix exponential while a numerical scheme is applied to the nonlinear part~$\Nbf$.
For IMEX schemes, an explicit formula is used to advance~$\Nbf$ while an implicit scheme is used to advance~$\Lbf$.
We show in this paper that the DFS method combined with IMEX schemes leads to $\mathcal{O}(nm\log nm)$ per time-step algorithms for both diffusive and dispersive PDEs, that exponential integrators achieve this complexity for diffusive PDEs only, and that IMEX schemes outperform exponential integrators in both cases.

<a href="http://www.chebfun.org/docs/guide/guide19.html"> spinsphere code</a>
<a href="http://www.ptrinh.com">Philippe Trinh</a>
<a href="http://www.math.ubc.ca/~ward/">Michael Ward</a> 
<a href="http://shvartsmanlab.com">Stanislav Shvartsman</a>
