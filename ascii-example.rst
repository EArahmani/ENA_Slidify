
Literate R programming with reST using ascii-package
====================================================

:Author: Matti Pastell <matti.pastell@helsinki.fi>
:website: http://mpastell.com

.. contents:: Table of Contents

Intro
------

This a simple example [#]_ of the usage of `ReStructuredText <http://docutils.sourceforge.net/rst.html>`_ for literate R programming with the ReST Sweave driver in the `ascii <http://eusebe.github.com/ascii/>`_ - package.


Example usage
--------------

The code chunks have the same options as the original **Sweave** driver. Here is *an example* of executing some code and adding a Figure:

Results in a table
__________________

::

  > library(MASS)
  > data(npk)
  > aov.npk <- aov(yield ~ block + N * P * K, npk)
  > print(ascii(summary(aov.npk)), "rest")


+-------------+-------+--------+---------+---------+--------+
|             | Df    | Sum Sq | Mean Sq | F value | Pr(>F) |
+=============+=======+========+=========+=========+========+
| block       | 5.00  | 343.30 | 68.66   | 4.45    | 0.02   |
+-------------+-------+--------+---------+---------+--------+
| N           | 1.00  | 189.28 | 189.28  | 12.26   | 0.00   |
+-------------+-------+--------+---------+---------+--------+
| P           | 1.00  | 8.40   | 8.40    | 0.54    | 0.47   |
+-------------+-------+--------+---------+---------+--------+
| K           | 1.00  | 95.20  | 95.20   | 6.17    | 0.03   |
+-------------+-------+--------+---------+---------+--------+
| N:P         | 1.00  | 21.28  | 21.28   | 1.38    | 0.26   |
+-------------+-------+--------+---------+---------+--------+
| N:K         | 1.00  | 33.13  | 33.13   | 2.15    | 0.17   |
+-------------+-------+--------+---------+---------+--------+
| P:K         | 1.00  | 0.48   | 0.48    | 0.03    | 0.86   |
+-------------+-------+--------+---------+---------+--------+
| Residuals   | 12.00 | 185.29 | 15.44   |         |        |
+-------------+-------+--------+---------+---------+--------+ 

Adding a figure
________________

::

  > x = rnorm(1000)
  > hist(x, freq = FALSE)
  > xax = seq(-10, 10, by = 0.1)
  > lines(xax, dnorm(xax, mean(x), sd(x)), col = 4, lwd = 2)


.. image:: ascii-example-002.jpg

.. [#] This is a footnote

