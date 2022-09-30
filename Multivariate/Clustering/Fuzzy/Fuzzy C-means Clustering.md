# Fuzzy C-means Clustering
假设将 $n$ 个样本 $\{x_1,x_2,\cdots,x_n\}$ 划分为 $c$ 类，其中 $x_i=(x_{i1},x_{i2},\cdots,x_{ip})'\quad(i=1,2,\cdots,n)$。样本 $x_i$ 属于 $g$ 类的模糊隶属度为 $u_{ig}$，由隶属度构成模糊矩阵 $\mathbf{U}=(u_{ig})\_{n\times c}$， $\mathbf{U}$ 满足 $\forall i=1,2,\cdots,n,\quad \sum_{g=1}^c u_{ig}=1$。记各类的类中心矩阵为 $\mathbf{V}=\{v_1,v_2,\cdots,v_c\}\in R^{pc}$。

给出
$$\sum_{i=1}^n \sum_{g=1}^c u_{ig}^m ||x_i-v_g||_A^2 \quad (m\ge 1)$$

FCM 聚类方法的核心是求解使上式达到最小值的 $\mathbf{U}$ 和 $\mathbf{V}$，即

$$\operatorname*{arg\,min}\_{U,V} \sum_{i=1}^n \sum_{g=1}^c u_{ig}^m ||x_i-v_g||\_A^2 \quad (m\ge 1)$$

使用交替优化法迭代求解上式的步骤为：
1. 给定 $m$、类的个数 $c$、最大迭代次数 $T$、精度 $\epsilon$
2. 初始化类中心矩阵 $\mathbf{V}_0$， $t=0$
3. 由 $\mathbf{V}\_{t-1}$ 计算 $\mathbf{U}\_t$
   $$u_{ig,t}=[\sum_{j=1}^c ({||x_i-v_{g,t-1}||\_A \over ||x_i-v_{j,t-1}||\_A })]^{-1}, \quad i=1,2,\cdots,n;\quad g=1,2,\cdots,c$$
5. 由 $\mathbf{U}\_t$ 计算 $\mathbf{V}\_t$
   $$v_{g,t}={\sum_{i=1}^n u_{ig,t}^m x_i \over \sum_{i=1}^n u_{ig,t}^m}, \quad g=1,2,\cdots,c$$
7. 如果 $||\mathbf{V}\_t-\mathbf{V}\_{t-1}||\le\epsilon \lor t>T$，停止迭代；否则跳回到第三步
8. 输出 $\mathbf{U}_t$ 和 $\mathbf{V}_t$