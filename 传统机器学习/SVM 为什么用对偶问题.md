一、对偶问题往往更容易计算

Solving the primal problem, we obtain the optimal W，but know nothing about the ai. In order to classify a query point X we need to explicitly compute the scalar product WT, which may be expensive if d is large.
Solving the dual problem, we obtain the ai (where ai = 0 for all but a few points - the support vectors). In order to classify a query point x, the calculate is very efficiently calculated if there are only few support vectors.

二、引入核函数（核技巧），从而推广到非线性问题

The most significant benefit from solving the dual comes when you are using the "Kernel Trick" to classify data that is not linearly separable in the original feature space.


