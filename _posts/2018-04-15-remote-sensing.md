---

layout: post
disqus: 'y'
title:  Remote sensing of clouds
---

The remote sensing of clouds is a 3D inverse transport problem in our practical life, which can be used to estimate the precipitation and monitor the movement of clouds for weather forecasting.

The problem is formulated as typical transport problem, only a few things to be remarked:

- Boundary condition, the boundary condition is the so-called incoming boundary condition, which determines how much radiation is imposed into the computational domain. The external radiation source is the sun. It can be simplified that the source is along a fixed angle. The data is measured at each boundary point with various outgoing angle.

- The scattering phase, which is made of two components, one is from the cloud itself, the other part is from the air density. We suppose the cloud has uniform scatter phase, then the scattering coefficient can be written as
$$p(x, w\cdot w') = a(x) p_1(w\cdot w') + b(z) p_2(w\cdot w')$$
where $a(x)$ denotes the thickness of the cloud in space and $b(z)$ denotes the scattering from air, which is only relevant to the altitude.

- The inversion, the typical method like discrete ordinate is solved in phase space, however, because of the strong anisotropic property of the Mie scattering, it might be a little more difficult to deal with $p_1$. The Rayleigh scattering is much smoother and has finite band-width in angular space. Forward solving is not hard, usually a few iterations will be enough, since the scattering effect is very strong when there is only a small portion of cloud. More challenging part is the inversion itself, based on gradient-based method, the problem needs to be solved multiple times, the problem is: how to make things run faster in the forward problem solving without extra time caching local variables.

- Optimization, the scheme is more empirical than theoretical. The source term is more smoother since it is angularly integrated, that will buy another 1/2 regularity. However, this might be a little bit misleading in some papers, the source term $S^n$ can be computed by using $a^n$ at the $n$-th iteration. Then fix the coefficient and use this to compute the next iteration, which is nit validated yet. But from some numerical experiments, this might be working for some reason, the iteration number could be large though.
