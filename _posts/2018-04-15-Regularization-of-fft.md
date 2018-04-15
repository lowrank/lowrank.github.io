---
layout: post
disqus: 'y'
title:  Regularization of FFT
---
Usually ``fft`` does not need such thing, since it is invertible, by its good companion, ``ifft``. However, when there is an augmentation in the physical domain from $[0, 1]^d$ to $[0, 2]^d$, with periodic extension. Such extension exists by defining

$$f(x_1, \dots, x_d) = f(y_1, \dots, y_d)$$

where $y_i = 2 - x_i$ if $x_i > 1$ or $y_i = x_i$ when $x_i < 1$.

For such periodic function, its ``fft`` in $d$-dimension space $[0,2]^d$ is trivial, since it is periodic, the Fourier series will converge pointwisely, the mismatch on boundary is taken care of by the extension. On the other hand, such verbose extension is not necessary, as long as the function can match the boundary values, the same scheme always works.

Well, ``fft`` forward mapping is always valid, since we are not removing any information. But backward is not trivial at all, because the mapping is not invertible. We are using the partially data to infer the Fourier transform, which is impossible. Suppose we can have additional assumption on the Fourier transform on the extended domain, then we can formulate a minimization scheme based on the prior knowledge.
