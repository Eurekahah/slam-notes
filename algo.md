SLAM算法总结：https://blog.csdn.net/weixin_44580210/article/details/120805017?spm=1001.2014.3001.5502

### 残差与误差的区别

- **误差**：通常指系统估计值与真实值之间的差异（但真实值未知，无法直接计算）。
- **残差**：是观测值与模型预测值之间的差异（实际可计算），是优化问题的直接输入。

### 雅可比矩阵

高维导数，告诉系统如何调整参数，才能最小化误差