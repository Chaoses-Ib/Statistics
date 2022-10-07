# Multidimensional Scaling
在使用 Classical MDS 时，我们要给出样本间的距离矩阵，MDS 会在低维空间中寻找一组点，使得各点间的欧氏距离与给定的样本距离矩阵最相似。Classical MDS 的 loss function 为：

$$
Strain_D(x_1,x_2,\cdots,x_N)=
({\sum_{i,j}(b_{ij}-x_i^Tx_j)^2
\over \sum_{i,j} b_{ij}^2})^{1\over 2}
$$

其中 $x_i$ 为低维空间中的点， $b_{ij}$ 是从样本距离矩阵 $D$ 求得的内积，计算式为

$$b_{ij}={1\over 2}({1\over n} (\sum_{i=1}^n d_{ij}^2 + \sum_{j=1}^n d_{ij}^2) - {1 \over n^2}\sum_{i=1}^n \sum_{j=1}^n d_{ij}^2 - d_{ij}^2)$$

记 $\mathbf{B}=\{b_{ij}\}$， $\mathbf{B}$ 也可以表示为

$$\mathbf{B}=-{1 \over 2} \mathbf{C} \mathbf{D}^{(2)} \mathbf{C}$$

其中 $\mathbf{C}=\mathbf{I}-{1\over n}\mathbf{J}\_n$， $\mathbf{I}$ 为单位矩阵， $\mathbf{J}\_n$ 是 $n\times n$ 的全一矩阵， $\mathbf{D}^{(2)}=\{d_{ij}^2\}$。