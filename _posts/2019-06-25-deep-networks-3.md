---
layout: post
title: "Deep networks and the Kolmogorov&ndash;Arnold superposition theorem"
date: 2019-06-26
---

In my latest paper, I proved a theorem about the <a href='http://en.wikipedia.org/wiki/Approximation_theory'>approximation</a> of <a href='https://en.wikipedia.org/wiki/Function_of_several_real_variables'>multivariate</a> continuous functions by <a href='http://en.wikipedia.org/wiki/Deep_learning'>deep ReLU networks</a>, for which the <a href='http://en.wikipedia.org/wiki/Curse_of_dimensionality'>curse of dimensionality</a> is lessened. My theorem is based on the <a href='http://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Arnold_representation_theorem'>Kolmogorov&ndash;Arnold superposition theorem</a>, and on the approximation of the inner and outer functions that appear in the superposition by very deep ReLU networks.

<h2>Kolmogorov&ndash;Arnold superposition theorem</h2>

At the second <a href='http://en.wikipedia.org/wiki/International_Congress_of_Mathematicians'>International Congress of Mathematicians</a> in Paris 1900, <a href='http://en.wikipedia.org/wiki/David_Hilbert'>Hilbert</a> presented ten of his <a href='http://en.wikipedia.org/wiki/Hilbert%27s_problems'>23 problems</a>, including the <a href='http://en.wikipedia.org/wiki/Hilbert%27s_thirteenth_problem'>13th problem</a> about equations of degree seven. He considered the following equation,

$$
x^7 + ax^3 + bx^2 + cx + 1 = 0,
$$

and asked whether its solution $$x(a,b,c)$$, seen as a function of the three parameters $$a$$, $$b$$ and $$c$$, can be written as the <a href='http://en.wikipedia.org/wiki/Function_composition'>composition</a> of functions of only two variables.

Hilbert's 13th problem was solved by <a href='http://en.wikipedia.org/wiki/Andrey_Kolmogorov'>Kolmogorov</a> and his 19 years old student <a href='http://en.wikipedia.org/wiki/Vladimir_Arnold'>Arnold</a> in a series of papers in the 1950s. Kolmogorov first proved in 1956 that any continuous function of several variables can be expressed as the composition of functions of three variables. His student Arnold extended his theorem in 1957; three variables were reduced to two. Kolmogorov finally showed later that year that only functions of one variable were needed. The latter result is known as the Kolmogorov--Arnold superposition theorem, and states that any continuous functions $$f:[0,1]^n\rightarrow\mathbb{R}$$ can be decomposed as

$$
f(x_1,\ldots,x_n) = \sum_{j=0}^{2n}\phi_j\left(\sum_{i=1}^n\psi_{i,j}(x_i)\right),
$$

with $$2n+1$$ continuous <i><b>outer</b></i> functions $$\phi_j:\mathbb{R}\rightarrow\mathbb{R}$$ (dependent of $$f$$) and $$n(2n+1)$$ continuous <i><b>inner</b></i> functions $$\psi_{i,j}:[0,1]\rightarrow\mathbb{R}$$ (independent of $$f$$). 

The Kolmogorov&ndash;Arnold superposition theorem was further improved in the 1960s and the 1970s. Lorentz showed in 1962 that the outer functions $$\phi_j$$ might be chosen to be the same function $$\phi$$, and replaced the inner functions $$\psi_{i,j}$$ by $$\lambda_i\psi_j$$, for some positive rationally independent constants $$\lambda_i\leq 1$$, while Sprecher replaced the inner functions $$\psi_{i,j}$$ by <a href='https://en.wikipedia.org/wiki/H%C3%B6lder_condition'>H&#246;lder continuous</a> functions $$x_i\mapsto\lambda^{ij}\psi(x_i+j\epsilon)$$ in 1965. Two years later, Fridman demonstrated that the inner functions could be chosen to be <a href='https://en.wikipedia.org/wiki/Lipschitz_continuity'>Lipschitz continuous</a>, but his decomposition uses $$2n+1$$ outer functions and $$n(2n+1)$$ inner functions. Finally, Sprecher provided in 1972 a decomposition with Lipschitz continuous functions $$x_i\mapsto\lambda^{i-1}\psi(x_i+j\epsilon)$$.

<h2>Approximation theory for deep ReLU networks</h2>

One of the most important theoretical problems in deep network approximation theory is to determine why and when deep networks lessen or break the curse of dimensionality, characterized by the $$\mathcal{O}(\epsilon^{-n})$$ growth of the network size $$W$$ as the error $$\epsilon\rightarrow0$$, in dimension $$n$$. 

In my paper, I use a variant of Sprecher's 1965 version of the theorem, which reads

$$
f(x_1,\ldots,x_n) = \sum_{j=0}^{2n}\phi_j\left(\sum_{i=1}^n\lambda_i\psi(x_i+ja)\right),
$$

for some constants $$\lambda_1=1>\lambda_2>\ldots>\lambda_n$$ and $$a=[(2n+1)(2n+2)]^{-1}$$, and with H&#246;lder continuous inner function $$\psi$$.

I first show that the outer functions may be approximated by Lipschitz continuous functions. Then, I prove that the inner and outer functions can be approximated with error $$\epsilon$$ by deep networks of size $$\mathcal{O}(\epsilon^{-\log n})$$ and $$\mathcal{O}(\epsilon^{-1/2})$$, respectively. The resulting network that approximates $$f$$ has depth and size $$\mathcal{O}(\epsilon^{-\log n})$$; the curse of dimensionality is lessened. However, the constants that appear in the esmiates may be considerably large, and the resulting network architecture is adaptive, since the network used in the proof depends on $$f$$ via the outer functions.
