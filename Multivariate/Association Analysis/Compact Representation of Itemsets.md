# Compact Representation of Itemsets
![](images/Compact%20Representation.png)

## Maximal Frequent Itemsets
A frequent itemset is maximal if none of its immediate supersets are frequent.

## Closed Itemsets
An itemset $X$ is closed if none of its immediate supersets has exactly the same support count as $X$.  An itemset is a closed frequent itemset if it is closed and its support is greater than or equal to $minsup$.

Closed itemsets provide a minimal representation of all itemsets without losing their support information.