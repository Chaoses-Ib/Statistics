# Relative Measures
Q:
- [ ] relative measures 是用来比较 clustering 的，那为什么不用两个 clustering 的 external/internal measures 来进行比较呢？

## Silhouette coefficient
Plot the $s_j$ values in descending order for each cluster, and to note the overall SC value for a paricular set of parameters, as well as clusterwise SC values:

$$SC_i=\frac{1}{n_i} \sum_{x_j\in C_i} s_j$$

## Cluster stability
The main idea behind cluster stability is that the clusterings obtained from several datasets sampled from the same underlying distribution as $D$ should be similar or "stable".

## Clustering tendency
Clustering tendency (or clusterability) aims to determine whether the dataset $D$ has any meaningful groups to begin with.