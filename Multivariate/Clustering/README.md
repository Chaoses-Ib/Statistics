# Clustering
**Clustering (cluster analysis, unsupervised classification)** is the task of grouping a set of objects in such a way that objects in the same group (called a **cluster**) are more similar (in some sense) to each other than to those in other groups (clusters).[^wiki] 聚类的基本方法是：假设样品之间存在一定的相似性，根据样品的观测指标（变量），找出能够表示样品间相似程度的统计量，根据这些统计量将相似度较高的样品各自聚合为一簇，形成一个聚类结果。

## Types of clustering
### Partitional or hierarchical
- Partitional
- Hierarchical

### Exclusive, overlapping or fuzzy
- Exclusive  
  Assign each object to a single cluster.
- Overlapping (Non-exclusive)  
  An object can simultaneously belong to more than one class.
- Fuzzy (Probabilitic)  
  Every object belongs to every cluster with a membership weight that is between 0 and 1.

### Complete or partial
- Complete
- Partial  
  Some objects in a data set may not belong to well-defined groups.

## Types of clusters
- Well-separated  
  Each object in a well-separated cluster is closer to every other object in the cluster to any object not in the cluster.
- Prototype-based  
  Each object in a prototype-based cluster is closer to the prototype defines the cluster than to the prototype of any other cluster.
  - Center-based  
    Use the most central point as the prototype.
- Graph-based  
  A graph-based cluster is a *connected component*, i.e., a group of objects that are connected to one another, but have no connection to objects outside the group.
  - Contiguity-based  
    Two objects are connected only if they are within a specified distance of each other.
- Density-based  
  A density-based cluster is a dense region of objects that is surrounded by a region of low density.

## Applications
聚类主要有两种功能，第一种是从数据中挖掘知识，利用聚类的结果增进我们对事物的认识，启发新的研究思路，比如物种聚类、基因聚类、疾病聚类、客户聚类；第二种是处理数据，可作为更大算法的一个子过程，比如总结数据、压缩数据、寻找近邻。

- Clustering for understanding
  - Biology: taxonomy, genes
  - Information retrieval: search engine
  - Climate: patterns in the atmosphere and ocean
  - Psychology and medicine: identify different subcategories of an illness or condition
  - Business: segment customers
- Clustering for utility
  - Summarization
  - Compression
  - Efficiently finding nearest neighbors

[^wiki]: [Cluster analysis - Wikipedia](https://en.wikipedia.org/wiki/Cluster_analysis)