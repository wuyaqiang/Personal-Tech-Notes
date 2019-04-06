从结构上来讲，LSTM结构更加复杂，GRU结构更简单。

GRU中只有 update gate 和 reset gate 两个门，并且把 LSTM 中的 cell state 和 hidden state 合并，只使用一个 hidden state。

从使用效果上来讲，两者都能缓解梯度消失问题，对上下文编码的效果没有太大差别。

有研究表明，两者在多个任务上的表现相当。

但是：

* GRU 的参数量更小，计算效率更高，训练速度更快。
* GRU 的内部结构更容易修改。
