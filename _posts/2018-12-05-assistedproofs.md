---
layout: post
title: "Computer-assisted proofs for PDEs"
date: 2018-12-05
---

A couple of weeks ago, I spent a few days at 
<a href="https://mcgill.ca/">McGill Univeristy</a> 
with <a href="http://www.math.mcgill.ca/jplessard/Home.html">Jean-Philippe Lessard</a>.
He introduced me to the world of computer-assisted proofs, which I briefly describe in this post. 

<h2>Theory</h2>

Suppose we want to find steady-state solutions of nonlinear time-dependent PDEs of the form

$$
u_t = F(u),
$$

for some smooth <a href="https://en.wikipedia.org/wiki/Differential_operator">operator</a> 
$$F:U\mapsto U'$$ between two
<a href="https://en.wikipedia.org/wiki/Banach_space">Banach spaces</a> $$U$$ and $$U'$$. 
This amounts to solve the nonlinear equation $$F(u) = 0$$.
We typically use a <a href="https://en.wikipedia.org/wiki/Spectral_method">spectral method</a> 
and interpret $$u$$ as an infinite vector of spectral 
coefficients and $$F$$ as an operator acting on those coefficients.

For finite $$N$$-dimensional problems $$F_N(u_N)=0$$ one would typically use 
<a href="https://en.wikipedia.org/wiki/Newton%27s_method">Newton's method</a> 
where one iterates the map

$$
T_N(u_N) = u_N - DF_N^{-1}(u_N)F_N(u_N).
$$

When the <a href="https://en.wikipedia.org/wiki/Jacobian_matrix_and_determinant">Jacobian</a> 
$$DF_N^{-1}(u_N)$$ is invertible, $$T_N$$ is a 
<a href="https://en.wikipedia.org/wiki/Contraction_mapping">contraction</a> and 
it allows us to prove that the numerical solution $$\bar{u}_N$$ 
is close to the true solution $$u_N$$. 
(Typically, $$u_N$$ would be the vector of coefficients in a spectral expansion.)

In an infinite-dimensional setting, Newton's method reads

$$
T(u) = u - DF^{-1}(u)F(u).
$$

However, working with the inverse $$DF^{-1}(u)$$ of the 
<a href="https://en.wikipedia.org/wiki/Fr%C3%A9chet_derivative">Fr&eacute;chet derivative</a> might be hard. 
Instead, one typically considers an approximation $$A$$ (independent of $$u$$) of $$DF^{-1}(u)$$ 
and looks at the <a href="https://en.wikipedia.org/wiki/Banach_fixed-point_theorem">fixed point</a> problem


$$
T(u) = u - AF(u).
$$

The main challenge is to chose $$A$$ such that $$T$$ is a contraction on some neighborhood 
of the unknown true solution. 

The idea behind computer-assisted proofs goes like this. 
First, compute a numerical solution $$\bar{u}_N$$ of the discretized $$N$$-dimensional
problem $$F_N(u_N)=0$$.
Second, reinterpret $$\bar{u}_N$$ as an element $$\bar{u}$$ of the infinite-dimensional space by 
''padding the vector of coefficients with an infinite number of zero.''
We expect the true solution $$u$$ to be close to $$\bar{u}$$ so we will chose $$A$$ 
to be an approximation of $$DF^{-1}(\bar{u})$$. 
The following theorem justifies this approach.

<b>Theorem (Radii polynomial approach in Banach spaces).</b>
<i>Let $$U$$ and $$U'$$ be Banach spaces. Denote the norm on $$U$$ by $$\Vert\cdot\Vert_U$$.
Consider bounded linear operators $$A^{\dagger}\in L(U,U')$$ and $$A\in L(U',U)$$.
Assume that $$F:U\mapsto U'$$ is $$C^1$$, $$A$$ is injective and $$AF:U\mapsto U$$.
Consider an approximate solution $$\bar{u}$$ of $$F(u)=0$$ (usually obtained using Newton's method on a finite-dimensional discretization.) 
Let $$Y_0$$, $$Z_0$$, $$Z_1$$ and $$Z_2$$ be positive constants satisfying</i>

$$
\Vert AF(\bar{u})\Vert_U \leq Y_0, \\
\hspace{-1cm}\Vert I - AA^\dagger\Vert_{B(U)}\leq Z_0, \\
\hspace{-2.5cm}\Vert A[DF(\bar{u})-A^\dagger]\Vert_{B(U)}\leq Z_1, \\
\hspace{2cm}\Vert A[DF(u)-DF(\bar{u})]\Vert_{B(U)}\leq Z_2r, \quad \textit{for all}\;\Vert u - \bar{u}\Vert_U\leq r,
$$
 
<i>where $$\Vert\cdot\Vert_{B(U)}$$ is the induced operator norm for bounded linear operators
from $$U$$ to itself. Define the radii polynomial</i>

$$
p(r) = Z_2 r^2 - (1-Z_1-Z_0)r + Y_0.
$$

<i>If there exists $$r_0>0$$ such that $$p(r_0)<0$$, then there exists $$u\in B_{r_0}(\bar{u})$$
satisfying $$F(u)=0$$.</i>

One of the main challenges in this framework is to construct such an operator $$A$$. 
(Note that $$A^\dagger$$ is an approximation of the Fr&eacute;chet derivative $$DF(\bar{u})$$. 
In practice we often start by selecting a good $$A^\dagger$$.)


<h2>An example in 1D</h2>

Consider the Allen--Cahn equation with periodic boundary conditions,

$$
u_t = F(u) = \epsilon^2 u_{xx} + u^3 - u.
$$

In Fourier space, the linear part $$Lu=\epsilon^2 u_{xx}-u$$ is diagonal with entries 
$$-\epsilon^2k^2 - 1$$, $$k\in\mathbb{Z}$$.

Let us denote by $$\bar{u}_{N}$$ the numerical solution obtained using wavenumbers $$k$$ 
between $$-N$$ and $$N$$ ($$2N+1$$ grid points)
and by $$DF_N(\bar{u}_N)$$ the $$(2N+1) \times (2N+1)$$ Jacobian matrix at $$\bar{u}_N$$, which we can compute.
In this case a good choice for $$A^\dagger$$ is

$$
A^\dagger =
\begin{pmatrix}
DF_N(\bar{u}_N) & 0 & 0 & \ldots \\
0 & -\epsilon^2(N+1)^2 - 1 & 0 & \ldots \\
0 & 0 & -\epsilon^2(N+2)^2 -1 & \ldots \\
\vdots & \vdots & \vdots & \ddots
\end{pmatrix}.
$$

The idea is that for large enough $$N$$ the Fr&eacute;chet derivative of $$L$$ 
will dominate the Fr&eacute;chet derivative of $$N$$. (Note that $$DL(u)=L$$.)
Therefore we can choose

$$
A =
\begin{pmatrix}
DF_N^{-1}(\bar{u}_N) & 0 & 0 & \ldots \\
0 & \frac{1}{-\epsilon^2(N+1)^2-1} & 0 & \ldots \\
0 & 0 & \frac{1}{-\epsilon^2(N+2)^2-1} & \ldots \\
\vdots & \vdots & \vdots & \ddots
\end{pmatrix}.
$$



