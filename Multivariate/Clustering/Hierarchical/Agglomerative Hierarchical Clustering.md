# Agglomerative Hierarchical Clustering
Start with the points as individual clusters and, at each step, merge the closest pair of clusters.

## Cluster proximity measures
- MIN (single link)  
  The proximity between the closest two points in diﬀerent clusters (the shortest edge between two nodes in diﬀerent subsets of nodes).
- MAX (complete link)  
  The proximity between the farthest two points in diﬀerent clusters.
- Group Average  
  The average pairwise proximities (average length of edges) of all pairs of points from diﬀerent clusters.
- Centroid method
- Ward's method  
  The proximity between two clusters in terms of the increase in the SSE that results from merging the two clusters.

### The Lance-Williams formula
$$p(R,Q)=\alpha_A\ p(A,Q) + \alpha_B\ p(B,Q) + \beta\ p(A,B) + \gamma |p(A,Q)-p(B,Q)|$$

where $p$ is a proximity function, $R$ is formed by merging clusters $A$ and $B$.

Cluster Proximity Measure | $\alpha_A$ | $\alpha_B$ | $\beta$ | $\gamma$
--- | --- | --- | --- | ---
Single Link | $\frac{1}{2}$ | $\frac{1}{2}$ | $0$ | $-\frac{1}{2}$
Complete Link | $\frac{1}{2}$ | $\frac{1}{2}$ | $0$ | $\frac{1}{2}$
Group Average | $\frac{m_A}{m_A+m_B}$ | $\frac{m_B}{m_A+m_B}$ | $0$ | $0$
Centroid | $\frac{m_A}{m_A+m_B}$ | $\frac{m_B}{m_A+m_B}$ | $\frac{-m_Am_B}{(m_A+m_B)^2}$ | $0$
Ward's | $\frac{m_A+m_Q}{m_A+m_B+m_Q}$ | $\frac{m_B+m_Q}{m_A+m_B+m_Q}$ | $\frac{-m_Q}{m_A+m_B+m_Q}$ | $0$

$m_A,m_B,m_Q$ are the number of points in clusters $A,B,Q$, respectively.