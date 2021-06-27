======================================================
NumExpr: Fast numerical expression evaluator for NumPy (modified version)
======================================================
:Author: Alexander K.
*Original package info:*

:Author: David M. Cooke, Francesc Alted, and others.
:Maintainer: Robert A. McLeod
:Contact: robbmcleod@gmail.com
:URL: https://github.com/pydata/numexpr
:Documentation: http://numexpr.readthedocs.io/en/latest/
:Travis CI: |travis|
:GitHub Actions: |actions|
:PyPi: |version|
:DOI: |doi|
:readthedocs: |docs|

.. |actions| image:: https://github.com/pydata/numexpr/workflows/Build/badge.svg
        :target: https://github.com/pydata/numexpr/actions
.. |travis| image:: https://travis-ci.org/pydata/numexpr.png?branch=master
        :target: https://travis-ci.org/pydata/numexpr
.. |docs| image:: https://readthedocs.org/projects/numexpr/badge/?version=latest
        :target: http://numexpr.readthedocs.io/en/latest
.. |doi| image:: https://zenodo.org/badge/doi/10.5281/zenodo.2483274.svg
        :target:  https://doi.org/10.5281/zenodo.2483274
.. |version| image:: https://img.shields.io/pypi/v/numexpr.png
        :target: https://pypi.python.org/pypi/numexpr

What is NumExpr?
----------------

NumExpr is a fast numerical expression evaluator for NumPy.  With it,
expressions that operate on arrays (like :code:`'3*a+4*b'`) are accelerated
and use less memory than doing the same calculation in Python.

In addition, its multi-threaded capabilities can make use of all your
cores -- which generally results in substantial performance scaling compared
to NumPy.

Last but not least, numexpr can make use of Intel's VML (Vector Math
Library, normally integrated in its Math Kernel Library, or MKL).
This allows further acceleration of transcendent expressions.


Full introductory page can ge found in the original repository: https://github.com/pydata/numexpr
^^^^^^^^^^^


Installation
------------

From wheels
^^^^^^^^^^^

NumExpr_mod is available for install via `pip` for a wide range of platforms and 
Python versions just like its original version. 
Installation can be performed as::

pip install git+https://github.com/MrCheatak/numexpr_mod.git#numexpr_mod


From Source
^^^^^^^^^^^

On most `Nix systems your compilers will already be present. However if you 
are using a virtual environment with a substantially newer version of Python than
your system Python you may be prompted to install a new version of `gcc` or `clang`.

For Windows, you will need to install the Microsoft Visual C++ Build Tools 
(which are free) first.The version depends on which version of Python you have 
installed:

https://wiki.python.org/moin/WindowsCompilers

For Python 3.6+ simply installating the latest version of MSVC build tools should 
be sufficient. Note that wheels found via pip do not include MKL support. Wheels 
available via `conda` will have MKL, if the MKL backend is used for NumPy.

See `requirements.txt` for the required version of NumPy.

NumExpr is built in the standard Python way::

  python setup.py build install
  

Usage
-----

In the modified version it is possible to precompile expressions for
continuous use:
  >>> a = np.arange(0, 10, 1)
  >>> b = np.arange(0, 5, 0.5)
  >>> expr = ne.cache_expression("a + b")
  >>> ne.evaluate_cached(expr)
  array([ 0. ,  1.5,  3. ,  4.5,  6. ,  7.5,  9. , 10.5, 12. , 13.5])

It is required that variables remain the same type when cached expression is used.

Documentation
-------------

Please see the official documentation of the original package at `numexpr.readthedocs.io <https://numexpr.readthedocs.io>`_.
Included is a user guide, benchmark results, and the reference API.


Authors
-------

Please see `AUTHORS.txt <https://github.com/pydata/numexpr/blob/master/AUTHORS.txt>`_.


License
-------

NumExpr is distributed under the `MIT <http://www.opensource.org/licenses/mit-license.php>`_ license.


.. Local Variables:
.. mode: text
.. coding: utf-8
.. fill-column: 70
.. End:
