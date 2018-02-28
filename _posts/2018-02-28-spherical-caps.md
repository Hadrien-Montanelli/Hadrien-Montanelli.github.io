---
layout: post
title: "Spherical caps in cell polarization (to be continued)"
date: 2018-02-27
---

<div style="text-align: center;">
	<img src="/blog/sphericalcaps1.png" style="width:614px;height:190px;">
</div>

I have just submitted a paper about the modelling of 
<a href="https://en.wikipedia.org/wiki/Embryogenesis">embrygonesis</a> with the
<a href="http://shvartsmanlab.com">Shvartsman group</a> at 
<a href="http://www.princeton.edu">Princeton University</a>.

Symmetry breaking is crucial for the development of virtually all living organisms.

Equations:
$$
\left\{
\begin{array}{l}
U_t = \frac{\epsilon_u^2}{r^2}\Delta U + k_bH(U - B)V - k_d U\quad\text{on $\partial\Omega$}, \\[5pt]
V_t = \epsilon_v^2\Delta V\quad\text{in $\Omega$}, \\[5pt]
\epsilon_v^2\nabla V\cdot n = -k_b H(U - B)V + k_d U
\end{array}
\right. 
$$

Nondimensionalizing:
$$
\begin{array}{l}
u=k_dU/k_bV_{max}, \; \tau = k_d t, \\[5pt]
\epsilon^2 = \epsilon^2_u/k_dr^2, \; \alpha=3k_b/2k_dr, \\[5pt]
\beta = k_dB/k_bV_{max}
\end{array}
$$

PDE: 
$$
u_\tau = \epsilon^2\Delta u + \Big(1 - \frac{\alpha}{2\pi}\bar{u}\Big)H(u - \beta) - u
$$

<div style="text-align: center;">
	<img src="/blog/sphericalcaps2.png" style="width:506px;height:682px;">
</div>

A local perturbation will form a single spherical cap.
Multiple competing perturbations will relax to a single cap.
Random initial conditions will also relax to a single cap.
