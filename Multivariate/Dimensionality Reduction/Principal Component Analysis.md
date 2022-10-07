# Principal Component Analysis
[Python implementation](Principal%20Component%20Analysis.ipynb):
```python
def pca_transform(x, n_components=None):
    x = np.array(x, copy=True)

    # 求协方差矩阵
    cov = np.cov(x, rowvar=False)

    # 对协方差矩阵进行特征分解，并按特征值大小降序排列
    eigen_values, eigen_vectors = np.linalg.eigh(cov)
    idx = np.argsort(eigen_values)[::-1]
    eigen_values = eigen_values[idx]
    eigen_vectors = eigen_vectors[:, idx]

    # 保留前n个特征向量
    if n_components is not None:
        eigen_vectors = eigen_vectors[:, :n_components]

    # 计算主成分
    x = x - x.mean(axis=0)
    x = np.dot(eigen_vectors.T, x.T).T
    
    return x
```