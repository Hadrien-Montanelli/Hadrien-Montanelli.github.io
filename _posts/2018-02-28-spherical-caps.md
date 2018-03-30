---
layout: post
title: "Spherical caps in cell polarization"
date: 2018-02-27
---

<div style="text-align: center;">
	<img src="/blog/sphericalcaps1.png" style="width:614px;height:190px;">
</div>

I have just submitted a paper about the modelling of 
<a href="https://en.wikipedia.org/wiki/Embryogenesis">embrygonesis</a> with the
<a href="http://shvartsmanlab.com">Shvartsman group</a> at 
<a href="http://www.princeton.edu">Princeton University</a>.
Let me review the main ideas of our work.

We proposed a new model for the formation of polarized patterns observed in
early embryogenesis of 
<a href="https://en.wikipedia.org/wiki/Caenorhabditis_elegans"> <i>C. elegans</i></a> 
where <a href="http://en.wikipedia.org/wiki/Conservation_of_mass">mass conservation</a> 
is the driving force.
In our model, a species $$V$$ moves freely in a <a href="http://en.wikipedia.org/wiki/Cell_(biology)">cell</a> 
$$\Omega$$ and reversibly adheres to the <a href="http://en.wikipedia.org/wiki/Cell_membrane">cell membrane</a> 
$$\partial\Omega$$. 
The membrane-bound species $$U$$ diffuses on the surface and recruits
more of itself to the membrane.
For a sphere of radius $$r$$, $$U$$ and $$V$$ satisfy the following equations,

$$
\left\{
\begin{array}{l}
U_t = \frac{D_U}{r^2}\Delta U + k_b[U_0 + H(U - \Gamma)]V - k_d U
\quad\text{on $\partial\Omega$}, \\[5pt]
V_t = D_V\Delta V\quad\text{in $\Omega$}, \\[5pt]
D_V\nabla V\cdot n = -k_b [U_0 + H(U - \Gamma)V] + k_d U,
\end{array}
\right. 
$$

for some constants $$D_U$$, $$D_V$$, $$k_b$$, $$k_d$$, $$\Gamma$$ and $$U_0$$.
Upon nondimensionalization by $$u=k_dU/k_bV_0$$, we obtain a single PDE

$$
u_\tau = \delta^2\Delta u + \Big(1 - \alpha\bar{u}\Big)\Big(\beta+H(u - \gamma)\Big) - u,
$$

with

$$
\begin{array}{l}
\tau = k_d t, 
\;\; \delta^2 = D_u/k_dr^2, 
\;\; \alpha=3k_b/2k_dr, \\[5pt]
\gamma = k_d\Gamma/k_bV_0,
\;\; \beta = k_dU_0/k_bV_0, \\[5pt]
\bar{u} = \text{average of $u$}.
\end{array}
$$

Using the algorithms presented in a 
<a href="http://localhost:4000/blog/2017/10/26/pdes-sphere">previous blog post</a>,
we showed that for arbitraty initial conditions, the only non-uniform long-term
behavior was a single axisymmetric sphereical cap:

<div style="text-align: center;">
	<img src="/blog/sphericalcaps2.jpg" style="width:480px;height:380px;">
</div>

We also showed that, starting from a constant initial condition, transient
convection is enough to start the polarization process:

<div style="text-align: center;">
	<img src="/blog/sphericalcaps3.jpg" style="width:765px;height:161.5px;">
</div>

These findings reinforce the idea that symmetry breaking is crucial for 
the development of all living organisms---paper's available online soon!