# Clustering Validation
Cluster validation and assessment encompasses three main tasks:
- Clustering evaluation: assess the goodness or quality of the clustering
- Clustering stability: understand the sensitivity of the clustering result to various algorithm parameters
- Clustering tendency: assess the suitability of applying clustering in the first place, that is, whether the data has any inherent grouping structure

There are a number of validity measures and statistics that have been proposed for each of the aforementioned tasks, which can be devided into three main types:
- [External Measures](External%20Measures.md)  
  External validation measures employ criteria that are not inherent to the dataset. This can be in form of prior or expert-specified knowledge about the cluster, for example, class labels for each point.
- [Internal Measures](Internal%20Measures.md)  
  Internal validation measures employ criteria that are derived from the data itself. For instance, we can use intracluster and intercluster distances to obtain measures of cluster compactness and separation.
- [Relative Measures](Relative%20Measures.md)  
  Relative validation measures aim to directly compare different clusterings, usually those obtained via different parameter settings for the same algorithm.

Terminology:
- External / Supervised / Exogeneous measures
- Internal / Unsupervised / Endogenous measures
- Relative measures