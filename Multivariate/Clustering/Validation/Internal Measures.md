# Internal Measures
The internal measures are based on the $n\times n$ **distance matrix** (proximity matrix), of all pairwise distances among the $n$ points:
$$W=\{ ||x_i-x_j|| \}^n_{i,j=1}$$
which is a symmetric matrix.

It can also be considered as the adjacency matrix of the weighted complete graph $G$. There is thus a close connection between the internal evaluation measures and the graph clustering objectives.

### Sihouette Coefficient
The sihouette coefficient is a measure of both cohesion and separation of clusters, and is based on the difference between the average distance to points in the closest cluster and to points in the same cluster. For each point $x_i$ we can calculate its silhouette coefficient $s_i$ as

$$s_i=\frac{\mu_{out}^{min}(x_i)-\mu_{in}(x_i)}
{\max{\{\mu_{out}^{min}(x_i),\mu_{in}(x_i)\}}}$$

where $\mu_{in}(x_i)$ is the mean distance from $x_i$ to points in its own cluster $\hat{y_i}$:

$$\mu_{in}(x_i)=\frac{\sum_{x_j\in C_{\hat{y_i}}, j\ne i } ||x_i-x_j||}
{n_{\hat{y_i}}-1}$$

and $\mu_{out}^{min}$ is the mean of the distances from $x_i$ to points in the closest cluster:

$$\mu_{out}^{min}(x_i)=\min_{j\ne \hat{y_i}}{
\frac{\sum_{x_j\in C_j } ||x_i-y||}
{n_j}
}$$

The $s_i$ value of a point lies in the interval $[-1,+1]$:
- $+1$: $x_i$ is much closer to points in its own cluster and is far from other clusters
- $0$: $x_i$ is close to the boundary between two clusters
- $-1$: $x_i$ is much closer to another cluster than its own cluster

The silhouette coefficient is defined as the mean $s_i$ value across all the points:

$$SC=\frac{1}{n}\sum_{i=1}^n s_i$$