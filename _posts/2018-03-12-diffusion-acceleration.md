---
layout: post
disqus: 'y'
title:  Diffusion Acceleration
---

It is widely accepted that diffusion model is the limiting model for transport equation, we omit numerous references here. The isotropic case says
$$v\cdot \nabla u + \sigma_t u  =\sigma_s U + q.$$
The approximating diffusion is (with Knudsen parameter equals 1),
$$-\nabla \cdot \frac{1}{\sigma_t} \nabla U + \sigma_a U = q.$$

The quick way to prove this is from the integral formulation,
$$U(x) = \int_{D}\frac{E(x, y)}{|x-y|} (\sigma_s(y) U(y) + q(y)) dy.$$

We expand $\sigma_t$, $\sigma_s$ and $U$ locally at $x$ as Taylor expansion, then for any interior point $x\in D$, the integral part can be truncated at second order term, which will give a $U$ term and a $\Delta U$ term.

We can continue to compute the higher order coefficients of $\nabla^k U$, which literally will give a high order PDE for $U$, in other words, $U$ should satisfy a high order elliptic PDE with only even orders.

So, instead of the well-known DSA, there are many other possibilities under this thread.
