---
layout: post
disqus: 'y'
title:  Inverse Problem on Point Source
---

The inverse problems on point source can be viewed as a model reduction, instead of considering the continuum case, the point sources (including dipole, multi-pole) are having less parameters which is more stable than the general reconstructions. The physical setting is usually 
$$
y = \mathcal{M} x + \eta
$$
or similar, where $$\mathcal{M}$$ is the measurement operator and $$\eta$$ is the additive noise (multiplicative noises are similar by taking logarithmic version).  

The quantity to recover is the $$x = \sum_{j=1}^S x_j\delta(w- \ w_j)$$, where $$S$$ is the number of point sources, $$x_j$$ is the amplitudes, $$\omega_j\in\mathbb{R}^n$$ are the spatial coordinates. The related inverse problems are studied in a variety of literatures. Numerically, the inversion is usually related to a small number of variables, within the linearization framework, the problem is to estimate the condition number of the forward operator. 

## Wave Equation with Homogeneous Media

In the wave equation, we can have several settings for the inverse problem with point sources. In the simplest acoustic wave equation with homogeneous medium assumption that
$$
u_{tt} = c^2 \Delta u + f(x)\delta(t - 0)
$$
where $$c$$ is constant, by normalization we can assume $$c\equiv 1$$, $$f$$ is the source term. The initial condition of $$u$$ can be assumed to be zeros for simplicity. Such problem can be solved through the Green’s function in the time domain easily.  In the frequency domain, we take the Fourier transform, 
$$
\Delta \hat{u}_k + (2\pi k)^2\hat{u}_k = -f(x)
$$
The full space Green’s function $$G(x, y) = \frac{e^{-i2\pi k\|x - y\|}}{4\pi \|x - y\|}$$. 



### Multiple Frequency Measurements

With multiple frequency measurements at a few far field locations, we can observe
$$
\hat{u}_k(z) = \int_{\mathbb{R}^3}  \frac{e^{-i2\pi k\|z - y\|}}{4\pi \|z - y\|} f(y) dy
$$
For point sources $$f$$ in the form as the previous $$x$$, the above measurement is 
$$
\hat{u}_k(z) = \sum_{j=1}^S x_j \frac{e^{-i2\pi k \|z - w_j\|}}{4\pi \|z - w_j\|}
$$
Suppose the frequency bandwidth is $$M$$ that $$k$$ ranges from $$0$$ to $$M$$, then above the question is to recover the point sources $$(x_j, w_j)$$ from the observation locations $$z\in Z$$.   The problem setting of the 1D case is also relevant to the super resolution. Physical model is from the wave equation in the homogeneous medium with a paraxial approximation that $$\|z - w_j\| \simeq R + \frac{r_j}{2R}$$ , where $$R$$ is the distance from $$z$$ to the sensor array, $$r_j$$ is the offset of the $$j$$-th sensor. In this case
$$
\hat{u}_k(z) = \sum_{j=1}^S x_j \frac{e^{-i2\pi k (R + r_j/(2R))}}{4\pi R}
$$


Let $$t_j = R + \frac{r_j}{2R}$$, and $$s_j = \frac{x_j}{4\pi R}$$, omit the $$z$$ in the above equation, we get the linear system 
$$
\hat{u}_k = \sum_{j=1}^S s_j e^{-i2\pi k t_j}
$$
Such equation can be solved through the ``Prony’s method``: Suppose the bandwidth $$M$$ is sufficiently large, then we try to find complex numbers $p_l$ that
$$
\sum_{l=0}^{S} \hat{u}_{k+l} p_l = \sum_{j=1}^S \sum_{l=0}^{S} s_j \rho_j^{k+l} p_l = (\sum_{j=1}^S s_j \rho_j^k )P(\rho_j) = \hat{u}_k P(\rho_j) = 0.
$$


 where $$P(x) = \sum_{l=0}^{S} x^l p_l $$. As long as the above equation is under-determined, we can always find the coefficients $$p_l$$ (unnormalized), the solution to the polynomial $$P(x) = 0$$ will be the roots $$\rho_j = \exp(-i2\pi t_j)$$. The noises will play a great role in this algebraic method since the stability of roots will be destroy due to the perturbation in data. The noises are formulated in additive way.
$$
\hat{u}_k  = \sum_{j=1}^S s_j e^{-i2\pi k t_j} + \eta_k
$$
To study the stability of the roots $$t_j$$, one just have to find out the condition number of the related Fourier matrix. 

 

### Single Frequency Measurements

Instead of taking multiple frequencies, when only one fixed frequency $$k$$, the point sources can be determined by partial data or full data from the Dirichlet to Neumann map on the boundary or far field data. Algebraic method creates a polynomial 
$$
P(x,y,z) = e^{i2\pi k z}\prod_{j=1}^S (x+iy - (x_j + iy_j))
$$
Such polynomial is a solution to the Helmholtz equation, the adjoint solution method can easily transfer the Dirichlet to Neumann data to the boundary integral.  Partial data case is much more complicated if one wants to deal with the algebraic approach, however the uniqueness is much easier without noises. 



## Wave Equation with Inhomogeneous Media

When the media is inhomogeneous but known, the multiple frequency approach will be difficult to find the Green’s formula though. However, if the perturbation in wave speed $$c$$ is localized small scatters, then ``Foldy-Lax`` approximation could be used.

TO BE CONTINUED.



## References

