---
layout: post
disqus: 'y'
title:  Singular integral
---

The singular integral are usually defined with principal value, with singular part removed.

$$\lim_{ϵ\to 0}\int_{D - B_{ϵ}} f(x) dx := P.V. \int_{D} f(x)dx$$

The singular integral, in general form, can be written as

$$\int_{D} \frac{f(x, v)}{\|x-y\|^{d}} u(y) dy$$

where $v = (x-y)/\|x-y\|$. The singular point $x = y$ is called pole, and $f(x, v)$ is the characteristic.

The integral's validity depends on $f(x, v)$'s behavior near singularity: continuity and integrability. Supposing $f$ is bounded and continuous in $x, v$, then we the principal value of the integral must satisfy $\int f(x, v) dv = 0$, then weakly singular integral's derivative will automatically satisfy such condition.

Such result is a special but very useful case from Calderon-Zygmund theorem and can be applied to many special kernels. However, it is quite hard to extend the result for higher regularity.
