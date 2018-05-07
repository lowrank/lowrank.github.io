---
layout: post
disqus: 'y'
title:  armadillo replaces matlab
---
Being long annoyed by lack of sufficient support on many functions, ``C++`` is always not a good choice for complete tool for numerical computing. Especially when many tools are used together, that is why ``MATLAB``'s mex interface is a relatively good match. The drawback is:  ``MATLAB`` is still slow on many important things and lacks flexibility on structural code such as OOP. The advantageous side is ``MATLAB`` is good at plotting.

I used to use ``Eigen`` a lot, and shift to my own linear algebra implementation for a while. Later I found ``armadillo`` is now much better than before. After a few tricks on acceleration of special functions, I believe it is a good way to replace ``MATLAB`` on general purpose. Writing the code in ``armadillo`` is not painful anymore.

Another benefit is: there is easy way to move into MATLAB with mex interface if necessary.

[TO BE CONTINUED]
