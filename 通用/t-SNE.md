t-distributed stochastic neighbor embedding (t-SNE)

t-SNE 是一种非线性降维算法，非常适用于高维数据降维到 2 维或者 3 维，并进行可视化。

相似对象的点之间的距离近，不相似的点之间距离远。

The t-SNE algorithm comprises two main stages.

First, t-SNE constructs a probability distribution over pairs of high-dimensional objects in such a way that similar objects have a high probability of being picked, whilst dissimilar points have an extremely small probability of being picked.

Second, t-SNE defines a similar probability distribution over the points in the low-dimensional map, and it minimizes the Kullback–Leibler divergence between the two distributions with respect to the locations of the points in the map. Note that whilst the original algorithm uses the Euclidean distance between objects as the base of its similarity metric, this should be changed as appropriate.

t-SNE 的缺点：

* t-SNE 的计算复杂度很高，在数百万个样本数据集中可能需要几个小时，而 PCA 可以在几秒钟或几分钟内完成。
* Barnes-Hut t-SNE 方法（下面讲）限于二维或三维嵌入。
* 算法是随机的，具有不同种子的多次实验可以产生不同的结果。虽然选择 loss 最小的结果就行，但可能需要多次实验以选择超参数。
* 全局结构未明确保留。这个问题可以通过 PCA 初始化点（使用 init ='pca'）来缓解。
