# Positive and Negative Predictive Values
![|1000](images/Positive%20and%20Negative%20Predictive%20Value%20Relationship.png) [^wiki]

- True Positives: The number of points that the classifier correctly predicts as positive.
  
  $$TP=n_{11}=|\{x_i|\hat{y_i}=y_i=c_1\}|$$
- False Positives: The number of points the classifier predicts to be positive, which in fact belong to the negative class.
  
  $$FP=n_{21}=|\{x_i|\hat{y_i}=c_1 \land y_i=c_2\}|$$
- False Negatives: The number of points the classifier predicts to be in the negative, which in fact belong to the positive class.
  
  $$FN=n_{12}=|\{x_i|\hat{y_i}=c_2 \land y_i=c_1\}|$$
- True Negatives: The number of points that the classifier correctly predicts as negative.
  
  $$TN=n_{22}=|\{x_i|\hat{y_i}=y_i=c_2\}|$$

True 是预测正确的，False 是预测错误的，True 和 False 后面是预测的结果。

- Error Rate
  
  $$Error\ Rate=\frac{FP+FN}{n}=1-Accuracy$$

## 推广到多分类
对于每个分类，可以将当前分类作为 Positive，所有其它分类作为 Negative。TP 为正确归类到当前分类，TN 为正确归类到其它分类，FP 为错误归类到当前分类，FN 为错误归类到其它分类。


[^wiki]: [Positive and negative predictive values - Wikipedia](https://en.wikipedia.org/wiki/Positive_and_negative_predictive_values)
