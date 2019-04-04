Precision 和 Recall值是既矛盾又统一的两个指标，为了提高 Precision 值，分类器需要尽量在 “更有把握” 时(即，提高分类阈值！)才把样本预测为正样本，但此时往往会因为过于保守而漏掉很多 “没有把握” 的正样本，导致 Recall 值降低。   

ROC（Receiver Operator Characteristic）曲线被广泛应用于二分类问题中来评估分类器的可信度，但是当处理一些高度不均衡的数据集时，PR 曲线能表现出更多的信息，发现更多的问题。
首先理解这四个基本指标：   

![](http://www.fullstackdevel.com/wp-content/uploads/2015/09/53451443447279.png)

ROC曲线中，是以FPR为x轴，TPR为y轴。   
PR曲线中，以Recall为x轴，Precision为y轴。 

绘制ROC曲线和PR曲线都是选定不同阈值，从而得到不同的x轴和y轴的值，画出曲线。   

在 ROC 空间，ROC 曲线越凸向左上方向效果越好，但是，PR 曲线是右上凸效果越好。  

当正负样本比例差距不大时，ROC和PR的趋势是差不多的，当正负样本比例差距很大时，ROC效果依然看似很好，但是PR曲线则会表现的比较差。  

所以，PR曲线在正负样本比例悬殊较大时，更能反映分类器的性能。  

当正负样本分布发生变化时，ROC 曲线的形状能够基本保持不变，而 P-R 曲线的形状一般会发生较剧烈的变化。这个特点让 ROC 曲线能够尽量降低不同测试集带来的干扰，更加客观地衡量模型本身的性能。这有什么实际意义呢？在很多实际问题中，正负样本数量往往很不均衡。  
比如，计算广告领域经常涉及转化率模型，正样本的数量往往是负样本数量的 1/1000 甚至 1/10000。若选择不同的测试集，P-R 曲线的变化就会非常大，而 ROC 曲线则能够更加稳定地反映模型本身的好坏。  
所以，ROC 曲线的适用场景更多，被广泛用于排序、推荐、广告等领域。但需要注意的是，选择 P-R 曲线还是 ROC 曲线是因实际问题而异的，如果研究者希望更多地看到模型在特定数据集上的表现，P-R 曲线则能够更直观地反映其性能。

AUC(Area Under Curve) 即指曲线下面积占总方格的比例。   
有时不同分类算法的 ROC 曲线存在交叉，因此很多时候用 AUC 值作为算法好坏的评判标准。面积越大，表示分类性能越好。

[https://zhuanlan.zhihu.com/p/34655990](https://zhuanlan.zhihu.com/p/34655990)  
(分析了ROC曲线的优缺点，以及ROC和PR的使用场景)

[http://www.fullstackdevel.com/computer-tec/data-mining-machine-learning/501.html](http://www.fullstackdevel.com/computer-tec/data-mining-machine-learning/501.html)   
(解释了ROC和PR曲线的概念与画法)
