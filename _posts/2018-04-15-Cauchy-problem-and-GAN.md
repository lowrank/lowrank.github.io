---
layout: post
disqus: 'y'
title:  Cauchy problem and GAN
---
The adversarial idea is to simultaneously improve the classifier and generator. In mathematics, this is very common idea in optimization, the input and output are both regularized. For some Cauchy problem, that we are given the initial field $U(0, x)$ and initial Neumann data $U_t(0, x)$, then the system will automatically generate the information for time $T$ as $U(T, x)$. Here $T$ can be a number of a set of time duration. However, such system might be very ill-posed if the data is simply at final time.

$$P(\beta, t) U = 0$$

Where $\beta$ is the meta-parameter for such system. The optimization scheme is usually formulated as

$$\min_{\beta} \|\widehat{U}(\beta, T) - U(T)\| + R(\beta)$$

Here we impose the constraints of the initial conditions by Lagrangian multiplier, then the problem turns to be

$$
\begin{equation}
\begin{aligned}
\min_{\beta}& \|\widehat{U}(\beta, T, x) - U(T, x)\| + R(\beta) \\&+ \lambda \|\widehat{U}(\beta, 0, x) - U(0, x)\| + \mu \|\widehat{U}_t(\beta, 0, x) - U_t(0, x)\|
\end{aligned}
\end{equation}
$$

Another way to look at such problem is: Instead of considering the single equation, we consider two equations with the same $\beta$,

- The first case is given Dirichlet data $u(0, x) = U(0, x)$ and measured data, then minimize the mismatch on Neumann data.

- The second case is given the Neumann data $v_t(0, x) = U_t(0, x)$ and measured data, then minimize the mismatch on Dirichlet data.

We combine them as

$$\min_{\beta} \|u_t(0, x) - U_t(0, x)\| + \|v(0,x) - U(0,x)\|$$

Such scheme can be seen as the GAN, the generator and the classifier now are in the roles with different equations. They are competing since one of them gets small easily while the other one will get large if there are no dedicate control.
