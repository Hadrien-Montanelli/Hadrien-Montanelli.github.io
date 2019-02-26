---
layout: post
title: "Deep networks and the curse of dimensionality"
date: 2017-12-22
---

<div style="text-align: center;">
	<img src="/blog/deepnet.jpg" style="width:595px;height:300px;">
</div>


I started working on <a href="http://en.wikipedia.org/wiki/Deep_learning">deep learning</a> 
models when I began my research at <a href="http//www.columbia.edu">Columbia University</a> in September 2017. 
Coming from the <a href="http://en.wikipedia.org/wiki/Approximation_theory">approximation theory</a>
world, I wanted to learn about their approximation propeties.
A few months down the road I have proven a <a href="http://arxiv.org/pdf/1712.08688.pdf">new theorem</a> concerning the approximation of 
<a href="http://en.wikipedia.org/wiki/Function_of_several_real_variables">multivariate functions</a> by deep ReLU networks.

Deep learning has been successfully applied to many fields including 
<a href="https://en.wikipedia.org/wiki/Computer_vision">computer vision</a>, 
<a href="https://en.wikipedia.org/wiki/Speech_recognition">speech recognition</a>, 
and <a href="http://en.wikipedia.org/wiki/Natural_language_processing">natural language processing</a>.
It is based on approximations by <i><b>deep networks</b></i>, as opposed to <i><b>shallow networks</b></i>.
The latter are neural networks with a single <i><b>hidden layer</b></i> and correspond to approximations $$f_N$$ of multivariate functions $$f:\mathbb{R}^d\rightarrow\mathbb{R}$$ of the form

$$
f_N(\boldsymbol{x}) = \sum_{i=1}^N \alpha_i \sigma(\boldsymbol{w}_i^T\boldsymbol{x} + \theta_i), \quad \alpha_i,\,\theta_i\in\mathbb{R},\, \boldsymbol{x},\boldsymbol{w}_i\in\mathbb{R}^d,
$$

for some <i><b>activation function</b></i> $$\sigma:\mathbb{R}\rightarrow\mathbb{R}$$.
The former are neural networks with one or more hidden layers, where each unit of each layer 
performs an operation of the form $$\sigma(\boldsymbol{w}\cdot\boldsymbol{x} + \theta)$$.
The <i><b>depth</b></i> of a network is the number of hidden layers, and the <i><b>size</b></i> 
is the total number of units.
Shallow networks have depth $$1$$ and their size is the number $$N$$ in the expansion above,
while deep networks usually have depth $$\gg 1$$.
Deep <i><b>ReLU</b></i> networks use the activation function $$\sigma(x) = \max(0,x)$$.

One of the most important theoretical problems is to determine why and when deep (but not shallow) networks
can lessen or break the <a href="https://en.wikipedia.org/wiki/Curse_of_dimensionality">curse of dimensionality</a>.
A possible way of addressing this problem is to focus on a particular set of functions which have a very
special (<a href="http://en.wikipedia.org/wiki/Function_composition">compositional</a> or 
<a href="https://en.wikipedia.org/wiki/Polynomial">polynomial</a>) structure, 
and to show that for this particular set deep networks perform extremely well.
I have followed a different route. 
I have considered a generic set of functions and proved new error estimates 
for which the curse of dimensionality is lessened by establishing a connection with 
<a href="http://en.wikipedia.org/wiki/Sparse_grid">sparse grids</a>.

For a real-valued function $$f$$ in $$\mathbb{R}^d$$ whose 
<a href="http://en.wikipedia.org/wiki/Smoothness">smoothness</a> is characterized by some integer $$m$$
(typically the order of <a href="https://en.wikipedia.org/wiki/Locally_integrable_function">integrable</a> derivatives), and for some prescribed accuracy $$\epsilon>0$$, 
one tries to show that there exists a neural network $$f_N$$ of size $$N$$ that satisfies

$$
\Vert f - f_N \Vert \leq \epsilon \quad \text{with} \quad N=\mathcal{O}(\epsilon^{-\frac{d}{m}}),
$$

for some norm $$\Vert\cdot\Vert$$. 
For deep networks, one also wants to find the asymptotic behavior of the depth 
as a function of the accuracy $$\epsilon$$.
Results of this form are standard approximation results that suffer from the curse of dimensionality.
For a small dimensions $$d$$, the size $$N$$ of the network increases at a reasonable rate as $$\epsilon$$ goes to zero.
However, $$N$$ grows <i><b>geometrically</b></i> with $$d$$.

The picture is different for deep networks.
My theorem shows that functions in the so-called Korobov spaces $$X^{2,p}(\Omega)$$ of mixed derivatives of order $$2$$ can be represented to accuracy $$\epsilon$$ by deep networks of depth 
$$\mathcal{O}(\vert\log_2\epsilon\vert\log_2d)$$ and size

$$
N=\mathcal{O}(\epsilon^{-\frac{1}{2}}\vert\log_2\epsilon\vert^{\frac{3}{2}(d-1)+1}(d-1)).
$$

The curse of dimensionality is not totally overcome but is lessened since 
$$d$$ only affects logarithmic factors $$\vert\log_2\epsilon\vert$$.
