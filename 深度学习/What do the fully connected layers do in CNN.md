问题：

全连接层起什么作用？为什么不在卷积层之后，立即用输出层？

回答：

The output from the convolutional layers represents high-level features in the data. While that output could be flattened and connected to the output layer, adding a fully-connected layer is a (usually) cheap way of learning non-linear combinations of these features.   
卷积层的输出表示的是数据的high-level特征。虽然输出可以被压平并连接到输出层，但是添加一个全连接层是学习这些特征的非线性组合的一种 (通常) 方便的方法。

Essentially the convolutional layers are providing a meaningful, low-dimensional, and somewhat invariant feature space, and the fully-connected layer is learning a (possibly non-linear) function in that space.   
NOTE: It is trivial to convert from FC layers to Conv layers. Converting these top FC layers to Conv layers can be helpful as this page describes.   
本质上，卷积层提供了一个有意义的、低维度的、固定的特征空间，而全连接层在这个特征空间中学习一个 (可能是非线性的) 函数。
