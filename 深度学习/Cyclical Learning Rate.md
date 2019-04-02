通常来讲，学习率在训练过程中一般是保持不变的，或者是为了在最优点附近减少波动，让学习率随着训练过程不断衰减。

循环学习率则提出了一个新的学习率变化规则，使学习率在训练过程中，周期性的递增然后递减。

其中涉及 epoch，iteration，cycle，stepsize 这四个概念：

epoch，即在整个训练集上训练一轮

iteration，指模型参数的一次更新

cycle，定义为学习率从低到高，再从高到低走一轮所用的 iteration 数

stepsize，指 cycle 迭代步数的一半



![img](https://app.yinxiang.com/shard/s53/res/15110dfb-ecd8-4382-a66b-77b94cd32d3b.png)

训练过程中，需要设置三个参数：stepsize，base_lr，max_lr

stepsize 的设置：

论文中实验认为，设为**一个 epoch 包含的 iteration 数量**的 2-10 倍较好，例如训练集50000个样本，batch_size为100，则一个 epoch 需要更新500次参数，即500个iteration，第二个 epoch 对应着 501 到 1000 个iteration，以此类推。这样的话，stepsize 就可以设为 1000-5000。

