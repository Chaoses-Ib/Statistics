# K-means
K-means is a prototype-based, partitional clustering technique that attempts to find a user-specified number of clusters $K$, which are represendted by their centroids.

## Basic K-means algorithm
```
Select K points as initial centroids.
repeat
  Form K clusters by assigning each point to its closest centroid.
  Recompute the centroid of each cluster.
until Centroids do not change
```
Space complexity: `O((m+K)n)`, where $m$ is the number of points and $n$ is the number of attributes.  
Time complexity: $O(I\times K\times m\times n)$, where $I$ is the number of iterations required for convergence, which is usually small.

[Python implementation](K-means.ipynb):
```python
def kmeans_cluster(df, k, max_iter=100):
    centroids = df.sample(k)
    for _ in range(max_iter):
        # 将每个点分配到距离最近的 centroid 所代表的 cluster
        distances = sk.metrics.DistanceMetric.get_metric('euclidean').pairwise(df, centroids)
        clusters = np.argmin(distances, axis=1)

        # 计算新的 centroids
        new_centroids = df.groupby(clusters).mean()

        # 如果 centroids 未发生改变，停止迭代，否则继续迭代
        if new_centroids.equals(centroids):
            break
        centroids = new_centroids
    return clusters
```

Proximity Measures | Centroid | Objective Function
--- | --- | ---
Manhattan $L_1$ | median | Minimize sum of the $L_1$ distance of an object to its cluster centroid
Squared Euclidean $L_2^2$ | mean | Minimize sum of the squared $L_2$ distance of an object to its cluster centroid
cosine | mean | Maximize sum of the cosine similarity of an object to its cluster centroid
Bregman divergence | mean | Minimize sum of the Bregman divergence of an object to its cluster centroid

### Choosing Initial Centroids
- Randomly  
  Often produce poor clusters.
- Randomly & multiple runs
- From hierarachical clustering  
  This approach often works well, but is practical only if the sample is relatively small and $K$ is relatively small compared to the sample size.
- Picking farthest  
  Outliers problem → Applied to a sample of the points
- K-means++

由于 K-均值聚类的结果依赖于初始点的选取，简单的随机选取经常会产生不佳的聚类结果，在实际应用 K-均值聚类时一般会使用多次随机选取或 K-means++ 算法。使用系统聚类的结果虽然也能取得较好的 K-均值聚类结果，但性能较低，不适合用于较大的数据集。

### Proximity Measures
- Euclidean distance ( $L_2$ distance)
- Manhattan ( $L_1$ distance)
- Documents → Jaccard measure

### Objective Functions
The goal of the clustering is typically expressed by an objective function that depends on the proximities of the points to one another or to the cluster centroids; e.g., minimize the *sum of squared error (SSE)* (the sum of squared distance of each point to its closest centroid).

### Centroids
After we have speciﬁed a proximity measure and an objective function, the centroid that we should choose can often be determined mathematically. For example, the centroid that minimizes the SSE of the cluster is the mean.

## Bisecting K-means
To obtain $K$ clusters, split the set of all points into two clusters, select one of these clusters to split, and so on, until $K$ clusters have been produced.

The ﬁnal set of clusters does not represent a clustering that is a local minimum with respect to the total SSE. Thus, we often reﬁne the resulting clusters by using their cluster centroids as the initial centroids for the standard K-means algorithm.

By recording the sequence of clusterings produced as K-means bisects clusters, we can also use bisecting K-means to produce a hierarchical clustering.