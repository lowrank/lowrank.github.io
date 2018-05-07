---
layout: post
disqus: 'y'
title:  Singularity of Green's function
---

It might be interesting to see how much change is there with the potential $V(x)$ perturbs. Take the Schrodinger equation $(\Delta + V) u = f$, we look for the Green's function with zero boundary condition.

When $V_1, V_2 \in \{f: f\in L^{\infty}(\Omega), \|f\|_{L^{\infty}} < \beta\}$, then we can look at the Lipmann-Schwinger equation,

$$G_1(x, y) - G_2(x,y) = \int_{\Omega} G_1(x, z) (V_1(z) - V_2(z)) G_2(z, y) dz$$

We know that when $x$ and $y$ are close, $G_1$ and $G_2$ will approach their singularities, however, the difference between them might be not singular at all. Since $V_1, V_2$ are bounded, then the local integral will be

$$\int_{\Omega} \frac{1}{\|x-z\|^{d-2}} \frac{1}{\|z-y\|^{d-2}} dz$$

The limiting case is $x=y$,

$$\int_{\Omega} \frac{1}{\|x-z\|^{2d-4}} dz$$

this is bounded as long as $d \le 3$. Somehow, it tells us something interesting, that the increment of Green's function is a more regular thing. Hopefully, we can deduce the low rank theory from there.
