---
layout: post
disqus: 'y'
title:  A layman review of DL
---
Being outsider for a long time on this topic, it still appears to be more like art instead of rigorous theories. I have been exposed to a few tutorials on this thread recently and I would like take a note with somewhat mathematical viewpoint.

- MLP (Multi-layer perceptron)

Given the input space $X$ and output space $Y$, the classification algorithms are falling into the basic question of "how to approximate the mapping from $X$ to $Y$" based on training data $\overline{Y} = f(\overline{X})$. (empirical information or prior information). A very strong assumption is the training data interpolates the exact mapping well enough.

Mathematically, it is a profound and historical problem. The approximation theory has been developed from centuries ago, and involves various levels of analysis. Again, the strong assumption on smoothness and large correlation scales reduce the parameter space dramatically. Such topic stems from the Kolmogorov width in 20th century, linear mapping $F:X\to Y$ is represented by a matrix $A$ when $X$ and $Y$ are finite dimensional space, i.e., $y = A x$. Such relation $A$ can be learned from the prior knowledge, which formulates $\tilde{y} = A \tilde
{x}$ when there is no noises, where $\tilde{y}$ and $\tilde{x}$ are from prior information, such matrix can be uniquely determined to certain rank, depending on the training data's rank by inverting a matrix. However, this inversion's accuracy depends on the condition number of the inputs matrix, when the inputs are highly correlated, then the inversion will tend to be quite unstable. Regularizations are usually taken to cure this problem, which is a variant of Bayesian approach, which is again, depending on the prior information. A special case in this approach is to use truncated SVD or so-called Tikhonov method, when there are random noises in the training data, such approach could be used to resolve the singular values above the noise level.

For nonlinear relation in the training data, it is more challenging. People are making additional assumptions such as the domain of $X$ is compact space embeded in $\mathbb{R}^n$ and the exact mapping is continuous, even differentiable. Given a minimization functional or cost functional $L$ on $Y\times Y$, the Kolmogorov approach states the problem in following form

$$\min_F L(\tilde{y}, F(\tilde{x}))$$

the infimum is taken over all low dimensional function $F$, low dimensional means $F(X)$ maps to a low dimensional topological geometry. Such problem somehow reveals the intrinsic dimensionality of the data. This problem is always a difficult one, and there are not too many reference on general approach. It can be proved that sufficient many hidden units in MLP can help to resolve any continuous mapping, however, it does not specify what kind of low dimensional MLP will be more efficient according to the inputs.

Another viewpoint for PDE analysts is to regard the mapping as evolution/deformation problem, the mapping is given by $F: \mathbb{R}^{+}\times X\to Y$ and the evolution from the training inputs to their label space is approximated by the transport equation, which describes the hyper-information propagation, assumption the medium is sufficiently smooth or with reasonable regularity, the transport problem can be formulated in a high dimensional space. The PDE is mostly described by H-J equation,

$$H(t, u, \nabla u, \nabla^2 u, \cdots, \nabla^k u) = 0$$

we suppose the input $u(0, x) \in X$ and the final output $u(\infty, x) \in Y$, in most cases of classification problems, $Y$ serves as discrete space and can be approximated by its empirical distribution $\tilde{Y}\subset \mathbb{R}$ or some other discrete valued function with delta function smoothed out. Suppose the flow are well defined everywhere and does not contain any caustics, then any particle along the characteristic will eventually arrive some point near the discrete values, in order to separate the values, we will require the preimage to be (almost) well-separated. Otherwise the topological fundamental group will be nontrivial.

- Autoencoder

This serves as some low dimensional projection or denoise projection. Mathematically, it is another way to write the Kolmogorov width.

$$\min_{F, B, W} \sup_{x} L(x - B\circ F(x))$$

with $F: X\to W$ and $B:W\to X$ and $W$ with sufficient low dimension. It might be interesting to design an efficient way to project the data points onto low dimensional space, however, it is not necessary that the labeled data are connected for each component. However, such discontinuity will impose wider band, which usually will increase the demand of high dimensional approximation.
