---
layout: post
disqus: 'y'
title:  Part I. Spectral, Regularity, Compactness
---

For simplicity, the measure is the usual measure. Lions assumes small measure in small angle by taking $\gamma\in(0, 2)$ that
$$\sup_{e} \mu(v\in R^n, |v\cdot e| \le \epsilon) \le C ϵ^{γ}.$$
Then the averaging lemma says, if $\psi(x, v)$ belongs to
$$W^p_{\pm} = \{ \psi \in L^p(X\times R^n); v\cdot\nabla \psi\in L^p(X\times R^n), \psi|_{\Gamma}\in L^p(\Gamma) \}$$
then velocity average of $\psi$ is in $W^{s, p}$, $s = \gamma / 2$ if $p=2$, and $s < \inf(p^{-1}, p'^{-1})\gamma$ if $p\neq 2$. The result is not difficult to prove, but the theorem is useful in some way. It can be shown that the regularity cannot be improved. For the sphere $|v| = 1$, we can see $\gamma = 1$, then the regularity for the average has $1/2$ improvement in differentiability. This also implies some compactness result.

In the context of neutron transport,
$$f_t + v\cdot \nabla f + \sigma(x, v) f = K f$$
where $\sigma(x, v)$ is the absorption coefficient or collision frequency. $K$ is linear collision operator, if these properties are time-independent, the semi-group theory can be used here and leads to spectral theory.

TO BE CONTINUED.
