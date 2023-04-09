# Collaborative Filtering
The process of identifying similar users and recommending what similar users like is called **collaborative ﬁltering**.

## Similarity Measures
- Jaccard distance
  
  只考虑是否评价，不考虑评分。
- Cosine distance

评分处理：
- Round ratings
  
  例如 $[1,2]\rightarrow 0,[3,4,5]\rightarrow 1$ 。
- Normalize ratings
  
  减去平均评分。

如果将未评分项目当作评分 0 的话，会导致未评分≈不喜欢。


为什么用 utility matrix 而不用 user profiles 来寻找相似用户？user profiles 不该更能反映本质吗？