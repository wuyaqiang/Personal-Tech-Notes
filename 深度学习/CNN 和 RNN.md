参考：[https://github.com/imhuay/Algorithm_Interview_Notes-Chinese/blob/master/A-%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0/B-%E4%B8%93%E9%A2%98-RNN.md
](https://github.com/imhuay/Algorithm_Interview_Notes-Chinese/blob/master/A-%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0/B-%E4%B8%93%E9%A2%98-RNN.md)

### CNN:
1. Take a fixed size input and generate fixed-size outputs
2. 适合处理图片和视频信息
3. 学习空间上的模式，例如识别图片中的components(lines, curves 等)，以及如何组合这些components，从而处理更加复杂的结构(faces, objects 等)。

### RNN:
1. Can handle arbitrary input/output lengths
2. Handle time-series information
3. 适合处理文本和语音信息
4. 相对于上面第3点，RNN学习的是时间序列上模式。

### LSTM 内部结构：
* 遗忘门：控制前一步记忆状态中的信息有多大程度被遗忘
* 输入门：控制当前计算的新状态以多大的程度更新到记忆状态中
* 输出门：控制当前的输出有多大程度取决于当前的记忆状态
* 细胞状态 Cell 由输入门和遗忘门共同决定

CNN是一种前馈神经网络，而RNN的工作模式是Saving the output of a layer and feeding this back to the input。

CNN仅仅只考虑当前的输入，而RNN不仅考虑了当前的输入，同时考虑了先前接受的输入，它能够记忆之前的多次输入。

最大步长为 T 的 RNN 展开后相当于一个共享参数的 T 层前馈网络。

RNN 因为每一个时间步都共享参数的缘故，容易出现数值溢出(即梯度消失和梯度爆炸)问题。

在文本分类中，CNN和RNN的对比：
[Comparative Study of CNN and RNN for Natural Language Processing](https://arxiv.org/pdf/1702.01923.pdf)

### RNN 存在的一些问题：
1. RNN 与目前的硬件加速技术不匹配： 训练 RNN 和 LSTM 非常困难，因为计算能力受到内存和带宽等的约束。简单来说，每个 LSTM 单元需要四个仿射变换，且每一个时间步都需要运行一次，这样的仿射变换会要求非常多的内存带宽。添加更多的计算单元很容易，但添加更多的内存带宽却很难——这与目前的硬件加速技术不匹配，一个可能的解决方案就是让计算在存储器设备中完成。
2. RNN 容易发生梯度消失，包括 LSTM： 在长期信息访问当前处理单元之前，需要按顺序地通过所有之前的单元。这意味着它很容易遭遇梯度消失问题；LSTM 一定程度上解决了这个问题，但 LSTM 网络中依然存在顺序访问的序列路径；实际上，现在这些路径甚至变得更加复杂

### RNN 中为什么采用 tanh 而不是 Relu 作为激活函数？
[知乎回答](https://www.zhihu.com/question/61265076)   
如果使用 Relu 作为 RNN 的激活函数，要注意将 w 初始化为单位矩阵。有实践证明，使用单位矩阵初始化 W 并使用 ReLU 作为激活函数在一些应用中，与 LSTM 有相似的结果。

### 为什么普通的前馈网络或 CNN 中不会出现梯度消失或爆炸的现象？
* 因为他们每一层的 W 不同，且在初始化时是独立同分布的，因此可以在一定程度相互抵消。即使多层之后一般也不会出现数值问题。

### 解决梯度消失问题：
* 残差结构
* 门控机制(LSTM, GRU)

### 解决梯度爆炸问题：clip_gradient (梯度截断):  
[https://hackernoon.com/gradient-clipping-57f04f0adae](https://hackernoon.com/gradient-clipping-57f04f0adae)
[https://machinelearningmastery.com/exploding-gradients-in-neural-networks/](https://machinelearningmastery.com/exploding-gradients-in-neural-networks/) 

更常用于RNN，为了缓解梯度爆炸问题

梯度在反向传播的过程中，可能发生梯度消失问题，这能够通过LSTM、GRU等结构来缓解，如果网络太深，也可能通过residual结构来缓解。

但是同时，也可能发生梯度爆炸问题，训练过程中，如果梯度变得非常大，则此时权重的更新过于迅猛，就容易导致loss发散、模型不稳定等， 梯度裁剪的直观作用就是让权重的更新限制在一个合适的范围

During experimentation, once the gradient value grows extremely large, it causes an overflow (i.e. NaN) which is easily detectable at runtime or in a less extreme situation, the Model starts overshooting past our Minima; this issue is called the Gradient Explosion Problem.








