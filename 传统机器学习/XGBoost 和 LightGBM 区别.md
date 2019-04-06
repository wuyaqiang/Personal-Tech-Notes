1.  树的切分策略不同：XGB 是 level-wise，而 LGB 是leaf-wise。

2.  实现并行的方式不同：XGB 是通过预排序的方式，LGB是通过直方图算法。

3.  LGB 内存占用更低， 速度更快。
