---
layout: post
title: "Gibbs phenomenon and Cesàro mean"
date: 2018-01-04
---

In this post I talk about a fascinating subject: the
<a href="http://en.wikipedia.org/wiki/Convergence_of_Fourier_series#Uniform_convergence">convergence of 
Fourier series</a> and the 
<a href="http://en.wikipedia.org/wiki/Gibbs_phenomenon">Gibbs phenomenon</a>.

<a href="http://en.wikipedia.org/wiki/Periodic_function">Periodic</a> 
<a href="http://en.wikipedia.org/wiki/Continuous_function">continuous</a>
functions $$f$$ 
of <a href="http://en.wikipedia.org/wiki/Bounded_variation">bounded variation</a> 
have a unique and 
<a href="http://en.wikipedia.org/wiki/Uniform_convergence">uniformly convergent</a>
<a href="http://en.wikipedia.org/wiki/Fourier_series">Fourier series</a>, 
that is, the <i><b>partial sums</b></i>

$$
f_n(\theta) = \sum_{k=0}^{n}a_k\cos(k\theta) + \sum_{k=1}^{n}b_k\sin(k\theta),
$$

with <i><b>Fourier coefficients</b><i>

$$
a_k = \frac{1}{\pi}\int_0^{2\pi}f(\theta)\cos(k\theta)d\theta, \quad
b_k = \frac{1}{\pi}\int_0^{2\pi} f(\theta) \sin(k\theta)d\theta,
$$

with $$1/\pi$$ changed to $$1/(2\pi)$$ for $$a_0$$, converge uniformly to $$f$$
and we write

$$
f(\theta) = \sum_{k=-\infty}^{\infty} c_ke^{ik\theta}.
$$

For functions $$f$$ that are merely of bounded variation, the convergence is only 
<a href="http://en.wikipedia.org/wiki/Pointwise_convergence">pointwise</a>:
at every point $$\theta$$, the partial sums converge to $$\frac{1}{2}[f(\theta^-) + f(\theta^+)]$$; 
in particular, these converge to $$f(\theta)$$ at every point of continuity.
What happens at points of 
<a href="http://en.wikipedia.org/wiki/Classification_of_discontinuities">discontinuity</a>?

A classical example is the square wave 

$$
f(\theta) = \frac{\pi}{4}\mathrm{sign}(\pi - \theta), \quad \theta\in[0,2\pi].
$$

This function is of bounded variation and discontinuous at $$0$$, $$\pi$$ and 
$$2\pi$$.
Its Fourier coefficients can be computed analytically and are given by

$$
a_k = 0, \quad b_{2k} = 0, \quad b_{2k+1} = \frac{1}{2k+1}.
$$

When we compute the partial sums for $$n=16,32,64,128$$ we obtain:
<div style="text-align: center;">
	<img src="/blog/gibbs1.jpg" style="width:516px;height:412px;">
</div>

This is the so called <i><b>Gibbs phenomenon</b></i>, which involves both the fact 
that the partial sums <i><b>overshoot</b></i> at a discontinuity and
that this overshoot does not die out as more terms are added to the sums. 
The overshoot at $$0$$, $$\pi$$ and $$2\pi$$ is known exactly and is given by

$$
\frac{1}{2}\int_0^{\pi}\frac{\sin(\theta)}{\theta}d\theta - \frac{\pi}{4} = \frac{\pi}{2}\times(0.089489872236\ldots),
$$

or about $$9\%$$ of the jump. 
Note that, as more terms are added, the position of the overshoot moves closer 
to the discontinuity. The Gibbs phenomenon is a very standard result that most 
applied mathematicians know. 

What is perhaps less known is a simple cure using the $$(C,1)$$
<a href="http://en.wikipedia.org/wiki/Ces%C3%A0ro_summation">Cesàro mean</a> of the
partial sums, which is simply
<a href="http://en.wikipedia.org/wiki/Arithmetic_mean">arithmetic mean</a> 
$$\sigma_n(\theta)$$ of the partial sums, i.e.,

$$
\sigma_n(\theta) = \frac{1}{n+1}\sum_{k=0}^{n}f_k(\theta).
$$

For integrable functions $$f$$, one can show that the Cesàro mean $$\sigma_n(\theta)$$ 
converges to $$\frac{1}{2}[f(\theta^-) + f(\theta^+)]$$; in particular, 
it converges to $$f(\theta)$$ at every point of continuity, 
and for continuous functions the convergence is uniform---this is 
<a href="http://en.wikipedia.org/wiki/Fej%C3%A9r%27s_theorem">Fejér's thereom</a>.
Moreover, if $$m\leq f(\theta)\leq M$$ then $$m\leq \sigma_n(\theta)\leq M$$. 
Therefore, the $$(C,1)$$ Cesàro mean does not show the Gibbs phenomenon, as 
the following figure illustrates:

<div style="text-align: center;">
	<img src="/blog/gibbs2.jpg" style="width:516px;height:412px;">
</div>

With <a href="http://home.cc.umanitoba.ca/~slevinrm/">Mikael Slevinsky</a>, 
we are using the $$(C,2)$$ Cesaràro mean for 
<a href="http://en.wikipedia.org/wiki/Spherical_harmonics">spherical harmonic</a> 
expansions on the sphere to post-process numerical solutions of nonlocal 
<a href="http://en.wikipedia.org/wiki/Partial_differential_equation">PDEs</a>---paper's 
coming soon!