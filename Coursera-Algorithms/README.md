# Coursera-algorithms课程总结
-
## 第一周

## Percolation

本周编程作业是Percolation，求解渗透问题，并通过Monte Carlo方法模拟找到渗透的阈值。

Percolation

用一个NxN的格子表示percolation系统，每一个格子是打开或者关闭，打开是白色关闭是黑色。 如果一个格子是full，首先他必须是打开的，然后表示从最顶上通过相连(4方向)的打开的格子可以渗透到这个位置。 当一个系统是percolates，表示能从最顶层渗透到最底层，也就是说，最底层存在打开的格子是full。

暴力方法时间复杂度太高，需要进行一些优化。

加入虚拟节点。首虚拟节点与第一层所有打开的元素相关联，尾虚拟节点和最后一层所有打开的节点相关联。如果首尾虚拟节点在一个集合中，那么系统是渗透成功的。 但是也会出现一个问题（backwash），因为有一些格子虽然从上面不能渗透到，但和尾虚拟节点连接后，他们也和首虚拟节点在一个集合了。

使用两个并查集避免backwash。一个只负责维护首虚拟节点，当进行isFull判断是否只考虑这个并查集，另一个并查集进行首尾虚拟节点的维护，用在percolates的判断中。

具体实现代码可见Percolation。

Monte Carlo simulation

Monte Carlo方法模拟多次渗透系统，知道渗透的阈值。代码可见PercolationStats。
