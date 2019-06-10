---
layout: post
disqus: 'y'
title:  pybind11 to replace matlab

---



Previously I post an article to claim that armadillo could be a way to replace matlab due to its adaptivity in numerical computation and its ease to use. However, I found it is also simple to adapt C++/C codes into Python nowadays by using the binding, unlike the ``cython``, using ``pybind11`` is just simpler. For most numerical computation, the binding from ``cython`` is quite a lot of work, ``swig`` or other approaches are not as simple as the ``pybind11``. 

The computation on a local machine will be quite simple to combine with previously existing Python codes using the ``Numpy`` interfaces provided by the ``pybind11``, the ``OpenMP`` combination is simple as well by releasing the lock manually. I intend to make a few practical examples to port  some of the ``matlab`` codes into the ``Python`` codes using such approach. 

Naive ``Python`` codes could be accelerated by some packages like ``numba`` , many other codes could be easily ported from certain ``C++`` implementations. I guess it could be a good way to bring numerical implementations from ``matlab`` community to ``Python`` community. Although MathWorks has made significant work to bring other language features into ``matlab``, but it is never simple and intuitive, there are a lot of undocumented things going on in ``matlab`` which made developing more like debugging. Hopefully, we could make the code iteration in a simper way by writing validation codes in ``matlab`` and port into ``c/c++``, then use ``pybind11`` to bind with ``Python``, which has the merits to a large variety of audience. 

